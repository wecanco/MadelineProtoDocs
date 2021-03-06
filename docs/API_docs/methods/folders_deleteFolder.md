---
title: folders.deleteFolder
description: Delete folder
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# Method: folders.deleteFolder  
[Back to methods index](index.md)


Delete folder

### Parameters:

| Name     |    Type       | Description | Required |
|----------|---------------|-------------|----------|
|folder\_id|[int](../types/int.md) | Folder ID | Yes|


### Return type: [Updates](../types/Updates.md)

### Can bots use this method: **NO**


### MadelineProto Example ([now async for huge speed and parallelism!](https://docs.madelineproto.xyz/docs/ASYNC.html)):


```php
if (!file_exists('madeline.php')) {
    copy('https://phar.madelineproto.xyz/madeline.php', 'madeline.php');
}
include 'madeline.php';

$MadelineProto = new \danog\MadelineProto\API('session.madeline');
$MadelineProto->start();

$Updates = $MadelineProto->folders->deleteFolder(['folder_id' => int, ]);
```

Or, if you're into Lua:

```lua
Updates = folders.deleteFolder({folder_id=int, })
```

