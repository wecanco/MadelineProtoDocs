---
title: payments.clearSavedInfo
description: Clear saved payments info
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# Method: payments.clearSavedInfo  
[Back to methods index](index.md)


Clear saved payments info

### Parameters:

| Name     |    Type       | Description | Required |
|----------|---------------|-------------|----------|
|credentials|[Bool](../types/Bool.md) | Clear credentials? | Optional|
|info|[Bool](../types/Bool.md) | Clear payment info? | Optional|


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

$Bool = $MadelineProto->payments->clearSavedInfo(['credentials' => Bool, 'info' => Bool, ]);
```

Or, if you're into Lua:

```lua
Bool = payments.clearSavedInfo({credentials=Bool, info=Bool, })
```

