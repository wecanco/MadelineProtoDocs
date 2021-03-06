---
title: messages.getAllChats
description: Get all chats (not supergroups or channels)
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# Method: messages.getAllChats  
[Back to methods index](index.md)


Get all chats (not supergroups or channels)

### Parameters:

| Name     |    Type       | Description | Required |
|----------|---------------|-------------|----------|
|except\_ids|Array of [int](../types/int.md) | Do not fetch these chats (MTProto id) | Yes|


### Return type: [messages\_Chats](../types/messages_Chats.md)

### Can bots use this method: **NO**


### MadelineProto Example ([now async for huge speed and parallelism!](https://docs.madelineproto.xyz/docs/ASYNC.html)):


```php
if (!file_exists('madeline.php')) {
    copy('https://phar.madelineproto.xyz/madeline.php', 'madeline.php');
}
include 'madeline.php';

$MadelineProto = new \danog\MadelineProto\API('session.madeline');
$MadelineProto->start();

$messages_Chats = $MadelineProto->messages->getAllChats(['except_ids' => [int, int], ]);
```

Or, if you're into Lua:

```lua
messages_Chats = messages.getAllChats({except_ids={int}, })
```

