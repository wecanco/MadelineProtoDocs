---
title: account.finishTakeoutSession
description: Finish account exporting session
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# Method: account.finishTakeoutSession  
[Back to methods index](index.md)


Finish account exporting session

### Parameters:

| Name     |    Type       | Description | Required |
|----------|---------------|-------------|----------|
|success|[Bool](../types/Bool.md) | Did the data export succeed? | Optional|


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

$Bool = $MadelineProto->account->finishTakeoutSession(['success' => Bool, ]);
```

Or, if you're into Lua:

```lua
Bool = account.finishTakeoutSession({success=Bool, })
```

