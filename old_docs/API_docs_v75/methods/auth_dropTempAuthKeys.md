---
title: auth.dropTempAuthKeys
description: Delete all temporary authorization keys except the ones provided
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# Method: auth.dropTempAuthKeys  
[Back to methods index](index.md)


Delete all temporary authorization keys except the ones provided

### Parameters:

| Name     |    Type       | Description | Required |
|----------|---------------|-------------|----------|
|except\_auth\_keys|Array of [long](../types/long.md) | The temporary authorization keys to keep | Yes|


### Return type: [Bool](../types/Bool.md)

### Can bots use this method: **YES**


### MadelineProto Example ([now async for huge speed and parallelism!](https://docs.madelineproto.xyz/docs/ASYNC.html)):


```php
if (!file_exists('madeline.php')) {
    copy('https://phar.madelineproto.xyz/madeline.php', 'madeline.php');
}
include 'madeline.php';

$MadelineProto = new \danog\MadelineProto\API('session.madeline');
$MadelineProto->start();

$Bool = $MadelineProto->auth->dropTempAuthKeys(['except_auth_keys' => [long, long], ]);
```

Or, if you're into Lua:

```lua
Bool = auth.dropTempAuthKeys({except_auth_keys={long}, })
```

