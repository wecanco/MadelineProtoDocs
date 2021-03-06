---
title: auth.sendInvites
description: Invite friends to telegram!
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# Method: auth.sendInvites  
[Back to methods index](index.md)


Invite friends to telegram!

### Parameters:

| Name     |    Type       | Description | Required |
|----------|---------------|-------------|----------|
|phone\_numbers|Array of [string](../types/string.md) | Phone numbers to invite | Yes|
|message|[string](../types/string.md) | The message to send | Yes|


### Return type: [Bool](../types/Bool.md)

### Can bots use this method: **NO**


### MadelineProto Example ([now async for huge speed and parallelism!](https://docs.madelineproto.xyz/docs/ASYNC.html)):


```php
if (!file_exists('madeline.php')) {
    copy('https://phar.madelineproto.xyz/madeline.php', 'madeline.php');
}
include 'madeline.php';

$MadelineProto = new \danog\MadelineProto\API('session.madeline');
$MadelineProto->start();

$Bool = $MadelineProto->auth->sendInvites(['phone_numbers' => ['string', 'string'], 'message' => 'string', ]);
```

Or, if you're into Lua:

```lua
Bool = auth.sendInvites({phone_numbers={'string'}, message='string', })
```


## Return value 

If the length of the provided message is bigger than 4096, the message will be split in chunks and the method will be called multiple times, with the same parameters (except for the message), and an array of [Bool](../types/Bool.md) will be returned instead.


### Errors this method can return:

| Error    | Description   |
|----------|---------------|
|MESSAGE_EMPTY|The provided message is empty|


