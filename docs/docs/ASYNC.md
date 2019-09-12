---
title: همزمانی
description: اکنون میدلاین پروتو برای پیشرفت سرعت باورنکردنی و پردازشرموازی امکانات از همزمانی بهره می برد.  
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# همزمانی

اکنون میدلاین پروتو برای پیشرفت سرعت باورنکردنی و پردازشرموازی امکانات از همزمانی بهره می برد.
 
با کمک [amphp](https://amphp.org), میدلاین پروتو API های AMPHP را بسته بندی و پیچیده می کند تا یک API  همزمانی مبتنی بر یک ژنراتور ساده تر ارائه دهد.

* [استفاده](#usage)
  * [فعال سازی API همزمانی میدلاین پروتو](#enabling-the-madelineproto-async-api)
  * [استفاده از API  همزمانی میدلاین پروتو](#using-the-madelineproto-async-api)
    * [همزمانی در کنترل رویداد](#async-in-event-handler)
    * [کنترل پاسخ به تماس همزمانی](#async-in-callback-handler)
    * [همزمانی پیچیده و بسته بندی شده](#wrapped-async)
    * [همزمانی چندگانه](#multiple-async)
    * [دسترسی به آرایه با همزمانی](#arrayaccess-async)
    * [نادیده گرفتن همزمانی](#ignored-async)
    * [مسدود سازی هزمانی](#blocking-async)
  * [API  های میدلاین پروتو و AMPHP](#madelineproto-and-amphp-async-apis)
    * [روش های کمک کننده](#helper-methods)
      * [خوابیدن همزمانی](#async-sleep-does-not-block-the-main-thread)
      * [خواندن خط همزمانی](#async-readline-does-not-block-the-main-thread)
      * [پژواک همزمانی](#async-echo-does-not-block-the-main-thread)
      * [artax میدلاین پروتو برای کلاینت HTTP](#madelineproto-artax-http-client)
      * [همزمانی forking](#async-forking-does-green-thread-forking)
      * [همزمانی  flock](#async-flock)
      * [ترکیب عملیات همزمانی](#combining-async-operations)
    * [API های حلقه ی همزمانی میدلاین پروتو](#async-loop-apis)
      * [حلقه](#loop)
      * [از سرگیری حلقه](#resumableloop)
      * [سیگنال حلقه](#signalloop)
      * [از سرگیری سیگنال حلقه](#resumablesignalloop)
      * [حلقه ی عمومی](#genericloop)

## استفاده

شاید سوال کنید که دقیقا همزمانی چیست,و چگونه بهتر از threading  یا multiprocessing?
همزمانی یک الگوی برنامه نویسی جدید است که به شما اجازه می دهد به راحتی کد های مسدود کننده را بنویسید طوری که از توابع مسدود کننده ی استاندارد استفاده میکنید, همه ی این ها بدون نیاز به سیستم های پیچیده ی تبادل پیام و کار با هماهنگ سازی کنترل برای برنامه های رشته ای, چیزی جز اضافه کردن سرباری و پیچیدگی به برنامه های شما ندارد و همه چیز را کندتر و مواجه با خطا می کند.
شاید شما با خود فکر کنید که خیلی باحال و همه چیز خوب است, اما این همزمانی چطور کار می کند؟ خب, چیزی که به نظر می آید بسیار آسان است.
به جای اینکه این کد را بنویسید:

```php
$file = $MadelineProto->download_to_dir($bigfile, '/tmp/');
```

می توانید اینجور بنویسید: 
```php
$file = yield $MadelineProto->download_to_dir($bigfile, '/tmp/');
```

### همین است.

واقعا راحت است,کافی است فقط شما yield اضافه کنید قبل صدا زدن روش یا متد های MadelineProto.
Yield به صورت خودکاراجرای عملکرد را به حالت تعلیق در می آورد, اجازه می دهدبه برنامهانجام دهد چیز های دیگری در حالی که فایل بارگیری می شود.
پس از بارگیری فایل, اجرای آن به صورت خودکار از آن نقطه ی دقیق تابع انجام می شود.

این به این معنی است که شما توانایی کنترل چندگانه ی بروزرسانی ها, بارگیری/بارگذاری فایل های چندگانه همه در یک روند, مانند اینکه شما درحال نوشتن کد های همزمان عادی + همه چیز را سریع تر می سازید.

اگر کد های شما هنوز روی همزمانی قدیم هست, نگران نباشید چیزی هست که بشودبه عقب بازگشت به صورت کامل. با این حال, من بسیار توصیه می کنم که شما به سمت همزمانی بروید, ناشی از کارایی بزرگ و موازی بودن فواید ها.

هشدار: همزمانی میدلاین پروتو با pthreads   یا  pcntl, پس لطفا phreads را حذف نصب کنید و از pcntl_fork استفاده نکنید در ربات های خود.


## فعال سازی API همزمانی میدلاین پروتو

yield فقط می تواند داخل تابع باشد که حالت همزمانی میدلاین پروتو فعال باشد.
برای انجام این کار, یا باید تابع همزمانی را فعال کتید, یا اگر میل بعضی از تماس ها را همزمانی کنید,پرچم فعال کننده ی همزمانی را به صورت جداگانه به هر تماس متد و دستور منتقل کنید.
این کد می تواند تمام تابع های میدلاین پروتو را برای حالت همزمانی فعال کند:

```php
$MadelineProto->async(true);
// ...
yield $MadelineProto->messages->sendMessage(...);
```

این کد می تواند حالت همزمانی را فقط برای یک تماس خاص و اختصاصی یک تابع میدلان پروتو را فعال کند( با اضافه کردن یک پارامتر آرایه جدید بعد از اتمام پارامتر های مورد نیاز): 
```php
yield $MadelineProto->messages->sendMessage(..., ['async' => true]);
```

## استفاده از API  همزمانی میدلاین پروتو

همان طور که قبلا گفتیم,شما فقط طوری می توانید اپراتورyield را استفاده کنید که داخل تابع باشد, اما هر تابع ای نه, برای مثال(کار نمی کند):
```php
$sm = function ($chatID, $message) use ($MadelineProto) {
    $id = (yield $MadelineProto->get_info($chatID, ['async' => true]))['bot_api_id'];
    $res = yield $MadelineProto->messages->sendMesssage(['peer' => $chatID, 'message' => "Message from: $id\n$message"], ['async' => true]);
    return $res;
};
$result = $sm('@danogentili', 'hi');
```

این کار نخواهد کرد, زیرا نتیجه ی تابعکه از yield استفاده می کند,مقدار بازگشتی نیست,بلکه یک [generator](https://www.php.net/manual/en/language.generators.overview.php) است,این همان چیزی است که async AMPHP API بر اساس آن است. اگر [generator](https://www.php.net/manual/en/language.generators.overview.php) از رویداد حلقه ی AMPHP گذشت نکند,اجرای تابع ادامه پیدا نخواهد کرد. وقتی میدلاین پروتو به طور همزمانی نتیجه ی get_info را بدست می آورد,اجرای تابع هرگز از سر گرفته نمی شود, و خط sendMessage هرگز فراخوانی نمی شود.
برای اجتناب کردن این مشکل, فقط تماس داشته باشید با تابع همزمانی در رویداد/پاسخ به بروزرسانی کنترل کننده, یا داخل تابع ای که تماس داشته اید توسط رویداد/پاسخ به بروزرسانی کنترل کننده, یاداخل تابع ای که از حلقه گذشت کند.
شما می توانید تماس داشته باشید با تابع همزمانی که خود شما ساخته اید,همراه با تابع های همزمانی دیگر.
[generator](https://www.php.net/manual/en/language.generators.overview.php) ها در میدلاین پروتو معادل وعده ها هستند,که الگویی هستند در که احتمالا در سایر زبان ها استفاده کرده اید.


### همزمانی در [کنترل رویداد](https://docs.madelineproto.xyz/docs/UPDATES.html#event-driven):
```php
$MadelineProto->async(true);
class EventHandler extends \danog\MadelineProto\EventHandler
{
    public function onAny($update)
    {
        if (isset($update['message']['out']) && $update['message']['out']) {
            return;
        }
        if (isset($update['message']['media']) && $update['message']['media']['_'] !== 'messageMediaGame') {
            yield $this->download_to_dir($update, '/tmp');
            yield $this->messages->sendMedia(['peer' => $update, 'message' => $update['message']['message'], 'media' => $update]);
        }

        $res = json_encode($update, JSON_PRETTY_PRINT);

        yield $this->sleep(3);

        try {
            yield $this->sm($update, "<code>$res</code>\nAsynchronously, after 3 seconds");
        } catch (\danog\MadelineProto\RPCErrorException $e) {
            \danog\MadelineProto\Logger::log((string) $e, \danog\MadelineProto\Logger::FATAL_ERROR);
        } catch (\danog\MadelineProto\Exception $e) {
            \danog\MadelineProto\Logger::log((string) $e, \danog\MadelineProto\Logger::FATAL_ERROR);
        }
    }
    public function sm($peer, $message)
    {
        yield $this->messages->sendMessage(['peer' => $peer, 'message' => $message, 'reply_to_msg_id' => isset($update['message']['id']) ? $update['message']['id'] : null, 'parse_mode' => 'HTML']);
    }
}
```

### همزمانی در [callback handler](https://docs.madelineproto.xyz/docs/UPDATES.html#callback):
```php
$MadelineProto->async(true);
$MadelineProto->setCallback(function ($update) use ($MadelineProto) {
    if (isset($update['message']['out']) && $update['message']['out']) {
        return;
    }
    yield $MadelineProto->sleep(3);
    yield $MadelineProto->messages->sendMessage(['peer' => $update, 'message' => 'Hi after 3 seconds']);
});
```

### همزمانی پیچیده و بسته بندی شده
```php
$MadelineProto->async(true);
$MadelineProto->loop(function () use ($MadelineProto) {
    yield $MadelineProto->messages->sendMessage(['peer' => '@danogentili', 'message' => 'hi']);
    // You can also have an asynchronous get_updates (deprecated) loop in here, if you want to; just don't forget to use yield for all MadelineProto functions.
});
```

شما می توانید یک قول را با یک تابع همزمانی را به تابع ی حلقه دار منتقل کنید,و مسدود می شود تا زمانی که حل شود.

### نادیده گرفتن همزمانی
```php
$MadelineProto->messages->sendMessage(['peer' => '@danogentili', 'message' => 'a'], ['async' => true]);
$MadelineProto->messages->sendMessage(['peer' => '@danogentili', 'message' => 'b'], ['async' => true]);
```
شما می توانید از توابع نسخه ی async میدلاین پروتو استفاده کنید بدون  yield اگر شما درخواست نمی کنید برای مسدود سازی, و شما نیاز ندارید به نتیجه ی تابع.
این مجاز است, اما ترتیب تماس ها و صدا زدن های تابع تضمین نمی شود: اگر می خواهید مطمئن شوید که ترتیب تماس ها و صدا زدن ها یکسان است, می توانید از [صف تماس ها](https://docs.madelineproto.xyz/docs/USING_METHODS.html#queues) استفاده کنید. نگاهی کنید به [async forking](#async-forking-does-async-green-thread-forking).

### همزمانی چندگانه
```php
yield $MadelineProto->messages->sendMessage([
    'multiple' => true,
    ['peer' => '@danogentili', 'message' => 'hi'],
    ['peer' => '@apony', 'message' => 'hi']
]);
```

این روش ترجیحی برای ترکیب چندین تماس و صدا زدن و فراخوانی به روش : از راه MadelineProto async WriteLoop تمام تماس و صدا زدن های متد را در یک ظرف ترکیب می کند و همه چیز را سریع تر می کند.
نتیجه این شاید باشد آرایه ای از نتیجه ها خواهد بود, که نوع آن با نوع روش بازگشت اصلی مشخص می شود) نگاهی کنید به [API docs](https://docs.madelineproto.xyz/API_docs) ).
ترتیب تماس ها و صدا زدن متد ها را می توان با استفاده از [صف تماس](USING_METHODS.html#queues),تضمین کرد)سمت سرور, نه توسط MadelineProto).


### دسترسی به آرایه با همزمانی

شما می توانید دسترسی به آرایه را بر روی وعده انجام دهید.

اکنون به جای اینکه این کار را کنید:  
```php
$id = (yield $MadelineProto->getPwrChat('danogentili'))['bot_api_id'];
```

شما می توانید به سادگی این کار را انجام دهید:
```php
$id = yield $MadelineProto->getPwrChat('danogentili')['bot_api_id'];
```

تنظیم ویژگی ها به طور همزمانی نیز پشتیبانی می شود)این یک نوع بی فایده و سود است اما اگر سفارش شما منطقی باشد, مثلا وقتی روشی که یک کلاس دسترسی به آرایه سفارشی را با یک روش مجموعه ای انجام می دهد که کاری جادویی انجام می دهد, مفید است.(

```php
$Id = yield $MadelineProto->getPwrChat('danogentili')['bot_api_id'] = 'pony';
```

صدور و تنظیم نشده پشتیبانی نمی شوند به دلیل این واقعیت که در PHP, صدور و تنظیم نشدن عملکرد های مناسبی نیستند بلکه ساختار های زبانی هستند) منطقی(.
شما باید این کار را انجام دهید در عوض:
 
```php
$set = isset((yield $MadelineProto->getPwrChat('danogentili'))['bot_api_id']);
```

یا

```php
$result = yield $MadelineProto->getPwrChat('danogentili');
$set = isset($result['bot_api_id']);
```

درواقع, دسترسی به آرایه روی ژنراتورهای خام هنوز پشتیبانی نمی شود جز اینکه آن ها را با استفاده از صدا زدن $MadelineProto->call در یک کوروتین ببندید:

```php
public function ponyAsync()
{
    return yield $MadelineProto->get_info('danogentili');
}
// public function onUpdateNewMessage....

// WILL NOT WORK
$set = yield $this->ponyAsync()['id'];

// Will work
$set = (yield $this->ponyAsync())['id'];

// Will work
$set = $MadelineProto->call(yield $this->ponyAsync())['id'];

public function pony()
{
    return $MadelineProto->call($this->ponyAsync());
}

// Will work
$set = yield $this->pony()['id'];
```


### مسدود سازی همزمانی
```php
$result = blocking_function();
```

بعضی وقت ها, شما باید تابع ی غیر همزمانی را صدا بزنید در کد های خود: این مجاز است در همزمانی MadelineProto, شما باید تابع خود را به صورت عادی بدون yield صدا بزنید. با این حال, شما نباید این عمل را نجام دهید( یا باید انجام دهید), زیرا این امر باعث می شود که همزمانی کاملا بی فایده باشد.
درحال حاضر AMPHP و MadelineProto, نسخه ی همزمانی curl,file_get_contents,MySQL,redis,postgres, و بسیاری از توابع بومی PHPارائه می دهند:


## API  های میدلاین پروتو و AMPHP

MadelineProto and AMPHP both provide a lot of async functions: all of MadelineProto's functions are async, for example; and AMPHP provides [multiple packages](https://amphp.org/packages) to work asynchronously with HTTP requests, websockets, databases (MySQL, redis, postgres, DNS, sockets and [much more](https://github.com/amphp/)!  
When using AMPHP libraries, you just have to use them with yield, no need to start the event loop, as long as you're running the functions inside MadelineProto's update handler/loop.  

Also, you should read the AMPHP docs, especially the [event loop docs](https://amphp.org/amp/event-loop/api): AMPHP provides multiple helper methods for executing actions repeatedly every N seconds in a non-blocking manner, or to defer execution of certain actions (aka async cron).  

### Helper methods

MadelineProto also provides a few generic async helper methods: when possible, always use MadelineProto's wrapped versions of the [amphp combinators](https://amphp.org/amp/promises/combinators) and [amphp helpers](https://amphp.org/amp/promises/miscellaneous) instead of original amphp methods (`all`, `any`, `some`, `first`, ...).  

#### Async sleep (does not block the main thread)
```php
yield $MadelineProto->sleep(3);
```

#### Async readline (does not block the main thread)
```php
$res = yield $MadelineProto->readLine('Optional prompt');
```

#### Async echo (does not block the main thread)
```php
yield $MadelineProto->echo('Hello'.PHP_EOL);
```

#### MadelineProto artax HTTP client

When using amphp's [artax](https://amphp.org/artax) to make high-speed asynchronous HTTP requests (downloading files, etc.), use MadelineProto's modified Artax client, instead.  
It automatically supports the socks/HTTP proxies specified in MadelineProto's settings (will use proxies only if the file can't be downloaded normally), and soon DoH for greater security.  

To use MadelineProto's artax client, instead of creating artax's default client:  
```php
$client = new Amp\Artax\DefaultClient;
```

Simply get MadelineProto's artax client:  
```php
$client = $MadelineProto->getHTTPClient();
```

From here it's like in the [artax docs](https://amphp.org/artax).  

MadelineProto also provides a simplified async version of `file_get_contents`:  
```php
$result = yield $MadelineProto->file_get_contents('https://myurl');
```

#### Async forking (does async green-thread forking)

Useful if you need to start a process in the background and you want throwed exceptions to surface up.  
These exceptions will exit the event loop, turning off the script unless you wrap `$MadelineProto->loop()` with a try-catch.  
Use it when you do not need the result of a method (see [ignored async](#ignored-async)), but you want eventual errors to crash the script.  
Otherwise, just use the method without yield.  

```php
// Exceptions will surface out of the event loop()
$MadelineProto->callFork($MadelineProto->messages->sendMessage([...]));
// Exceptions will be ignored
$MadelineProto->messages->sendMessage([...]);

// Like the first one, but the call will be deferred to the next event loop tick
$MadelineProto->callForkDefer($MadelineProto->messages->sendMessage([...]));
```

Ignoring exceptions is usually not good practice, so it's best to wrap the method you're calling in a closure with a try-catch with some error handling code inside of it, calling it right after that and passing it to callFork:

```php
$MadelineProto->callFork((function () use ($MadelineProto) {
    try {
        $MadelineProto->messages->sendMessage([...])
    } catch (\Exception $e) {
        // Handle by logging and stuff
    }
})());
```

#### Async flock

```php
$unlock = yield $MadelineProto->flock($filePath, LOCK_SH);
try {
    // ...
} finally {
    $unlock();
}
```

This will asynchronously wait for a lock on `$filePath` (creating it if it doesn't exist).  
The locking mode can be `LOCK_SH` (shared locks), `LOCK_EX` (exclusive locks), as with the PHP `flock` function.  
A third optional parameter can be set, to specify a polling interval in seconds (0.1 by default).  

#### Combining async operations

These methods can be used to execute multiple async operations simultaneously and wait for the result of all of them.  
Each method has different error handling techniques, see the [amphp docs](https://amphp.org/amp/promises/combinators).  
Note that if you just take the result of these methods without yielding it, you can use it as a normal promise/generator.  

**Note**: this is not the recommended method to make multiple method calls on the same instance of MadelineProto; use this only for non-API methods like `start()`; for API methods, use [multiple async](#multiple-async).  

```
$promise1 = $MadelineProto->messages->sendMessage(...);
$promise2 = $MadelineProto->messages->sendMessage(...);
// $promise3 = ...;

// Equivalent to Amp\Promise\all(), but works with generators, too
$results = yield $MadelineProto->all([$promise1, $promise2, $generator3]);

// Equivalent to Amp\Promise\first(), but works with generators, too
$results = yield $MadelineProto->first([$promise1, $promise2, $generator3]);

// Equivalent to Amp\Promise\any(), but works with generators, too
$results = yield $MadelineProto->any([$promise1, $promise2, $generator3]);

// Equivalent to Amp\Promise\some(), but works with generators, too
$results = yield $MadelineProto->some([$promise1, $promise2, $generator3]);
```

#### Handling timeouts

These methods can be used to wait for a certain amount of time for a result, and then throw an `Amp\TimeoutException` or simply continue execution if no result was obtained.  

```
// Waits for the result for 2 seconds and then throws an \Amp\TimeoutException
$result = yield $MadelineProto->timeout($promise, 2)

// Waits for the result for 2 seconds, returns the result or null (which is the result of sleep())
$result = yield $MadelineProto->first([$promise, $MadelineProto->sleep(2)]);
```

### Async loop APIs

MadelineProto provides a very useful async loop APIs, for executing operations periodically or on demand.  
It's a more flexible and powerful alternative to AMPHP's [repeat](https://amphp.org/amp/event-loop/api#repeat), allowing dynamically changeable repeat periods, resumes and signaling.  
All loop APIs are defined by one or more [interfaces](https://github.com/danog/MadelineProto/tree/master/src/danog/MadelineProto/Loop): however, to use them, you would usually have to extend only one of the [abstract class implementations](https://github.com/danog/MadelineProto/tree/master/src/danog/MadelineProto/Loop/Impl).  

#### Loop

A basic loop, capable of running in background (asynchronously) the code contained in the `loop` function.  

[Interface](https://github.com/danog/MadelineProto/blob/master/src/danog/MadelineProto/Loop/LoopInterface.php):  
```php
namespace danog\MadelineProto\Loop;

interface LoopInterface
{
    /**
     * Start the loop.
     *
     * @return void
     */
    public function start();

    /**
     * The actual loop.
     *
     * @return void
     */
    public function loop();

    /**
     * Get name of the loop
     *
     * @return string
     */
    public function __toString(): string;
}
```

Usually one would extend the [Loop implementation](https://github.com/danog/MadelineProto/blob/master/src/danog/MadelineProto/Loop/Impl/Loop.php).  
The loop function will be run only once, every time the `start` method (already implemented in the abstract Impl class we're extending) is called.  
The `start` method returns a promise that resolves when the loop finishes running.  
Multiple calls to `start` will be ignored, logging an error and returning `false` instead of `true`.  
You can use the `isRunning` method to check if the loop is already running.  
The `__toString` method still has to be implemented in order to get the name of the loop, that will be used by the MadelineProto logging mechanism every time the loop starts/exits/fails to start.  
By default, an instance of MadelineProto MUST be passed to the constructor of the function, or **if** a custom constructor is defined, the `$this->API` property MUST be set to an instance of MadelineProto.  

```php
use danog\MadelineProto\Loop\Impl\Loop;
class MyLoop extends Loop
{
    private $callable;
    public function __construct($API, $callable)
    {
        $this->API = $API;
        $this->callable = $callable;
    }
    public function loop()
    {
        $MadelineProto = $this->API;
        $logger = &$MadelineProto->logger;
        $callable = $this->callable;

        $result = null;
        while (true) {
            $params = yield $callable($result);
            $result = yield $MadelineProto->messages->sendMessage($params);
        }
    }
    public function __toString(): string
    {
        return "my custom loop";
    }
}
```

The loop can be instantiated and `start()`ed, and this will automatically run the code in the loop in background.  
If, however, only your loop is started (without an event handling loop), you have to pass the promise returned by `$loop->start()` to `$MadelineProto->loop`.  
Do NOT do this if you've already started `$MadelineProto->loop()`.  
```php
$loop = new MyLoop;
$MadelineProto->loop($loop->start());
```

#### ResumableLoop

A way more useful loop that exposes APIs to pause and resume the execution of the loop, both from outside of the loop, and in a cron-like manner from inside of the loop.  

[Interface](https://github.com/danog/MadelineProto/blob/master/src/danog/MadelineProto/Loop/ResumableLoopInterface.php):  
```php
namespace danog\MadelineProto\Loop;

interface ResumableLoopInterface extends LoopInterface
{
    /**
     * Pause the loop.
     *
     * @param int $time For how long to pause the loop, if null will pause forever (until resume is called from outside of the loop)
     *
     * @return Promise
     */
    public function pause($time = null): Promise;

    /**
     * Resume the loop.
     *
     * @return void
     */
    public function resume();
}
```

Usually one would extend the [ResumableSignalLoop implementation](https://github.com/danog/MadelineProto/blob/master/src/danog/MadelineProto/Loop/Impl/ResumableSignalLoop.php).  
An example implementation can be seen in the [ResumableSignalLoop section of this page](#resumablesignalloop).  

#### SignalLoop

Yet another loop interface that exposes APIs to send signals to the loop, useful to force the termination of a loop from the outside, or to send data into it.  

[Interface](https://github.com/danog/MadelineProto/blob/master/src/danog/MadelineProto/Loop/SignalLoopInterface.php):  
```php
namespace danog\MadelineProto\Loop;

interface SignalLoopInterface extends LoopInterface
{
    /**
     * Resolve the promise or return|throw the signal.
     *
     * @param Promise $promise The origin promise
     *
     * @return Promise
     */
    public function waitSignal($promise): Promise;

    /**
     * Send a signal to the the loop.
     *
     * @param Exception|any $data Signal to send
     *
     * @return void
     */
    public function signal($data);
}

```

Usually one would extend the [ResumableSignalLoop implementation](https://github.com/danog/MadelineProto/blob/master/src/danog/MadelineProto/Loop/Impl/ResumableSignalLoop.php).  
An example implementation can be seen in the [ResumableSignalLoop section of this page](#resumablesignalloop).  
If you want, you can also extend only the [SignalLoop implementation](https://github.com/danog/MadelineProto/blob/master/src/danog/MadelineProto/Loop/Impl/SignalLoop.php), but usually a combination of the SignalLoop and ResumableLoop implementations is used, so read on to find out how to do that.  

#### ResumableSignalLoop

This is what you would usually use to build a full async loop.  
All loop interfaces and loop implementations are combined into one single abstract class you can extend.  

```php
use danog\MadelineProto\Loop\Impl\ResumableSignalLoop;
class MySuperLoop extends ResumableSignalLoop
{
    private $timeout;
    public function __construct($API, $timeout)
    {
        $this->API = $API;
        $this->timeout = $timeout;
    }
    public function loop()
    {
        $MadelineProto = $this->API;
        $logger = &$MadelineProto->logger;

        while (true) {
            $t = time();

            $result = yield $this->waitSignal($this->pause($this->timeout));
            if ($result <= 0) {
                return;
            } else if ($result > 0) {
                $this->timeout = $result;
            }
            
            $t = time() - $t;
            
            $result = yield $MadelineProto->messages->sendMessage(
                [
                    'peer'    => '...',
                    'message' => "Resumed after $t seconds of timeout"
                ]
            );
        }
    }
    public function __toString(): string
    {
        return "my cron signal loop";
    }
}
```

[ResumableSignalLoop implementation](https://github.com/danog/MadelineProto/blob/master/src/danog/MadelineProto/Loop/Impl/ResumableSignalLoop.php).  
As with the [Loop](#loop).  

The difference now is that you can use the `pause` method to pause execution of the loop for a certain period of time (in seconds, supports decimals).  
If `null` is passed, execution will be suspended forever (or until `resume` is called from outside of the loop).  

If the promise returned by `pause` (or by any other async method) is passed to `waitSignal`, and the result is yielded, execution will be suspended for the specified amount of time|forever, or until a signal is received through the `signal` method.  
The passed signal will then be returned as result of the `waitSignal` method, and can be used to stop the loop, or simply as a message exchange mechanism.  

#### GenericLoop

If you want a simpler way to use the `ResumableSignalLoop`, you can use the [GenericLoop](https://github.com/danog/MadelineProto/blob/master/src/danog/MadelineProto/Loop/Generic/GenericLoop.php).  
The constructor accepts three parameters:
```php
    /**
     * Constructor
     *
     * @param \danog\MadelineProto\API $API Instance of MadelineProto
     * @param callback $callback Callback to run
     * @param string $name Fetcher name
     */
    public function __construct($API, $callback, $name) { // ...
```

Example:
```php
use danog\MadelineProto\Loop\Generic\GenericLoop;
$loop = new GenericLoop(
    $MadelineProto,
    function () {
        yield $this->API->messages->sendMessage(['peer' => '...', 'message' => 'Hi every 2 seconds']);

        return 2;
    },
    "My super loop"
);
$loop->start();
```
The callback will be bound to the GenericLoop instance: this means that you will be able to use `$this` as if the callback were actually the `loop` function (you can access the API property, use the pause/waitSignal methods & so on).  
The return value of the callable can be:  
* A number - the loop will be paused for the specified number of seconds
* `GenericLoop::STOP` - The loop will stop
* `GenericLoop::PAUSE` - The loop will pause forever (or until the `resume` method is called on the loop object from outside the loop)
* `GenericLoop::CONTINUE` - Return this if you want to rerun the loop without waiting

If the callable does not return anything, the loop will behave is if `GenericLoop::PAUSE` was returned.  

<a href="https://docs.madelineproto.xyz/docs/CREATING_A_CLIENT.html">Next section</a>