---
title: messages.getChats
description: Get info about chats
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# Method: messages.getChats  
[Back to methods index](index.md)


Get info about chats

### Parameters:

| Name     |    Type       | Description | Required |
|----------|---------------|-------------|----------|
|id|Array of [InputChat](../types/InputChat.md) | The MTProto IDs of chats to fetch info about | Yes|


### Return type: [messages\_Chats](../types/messages_Chats.md)

### Can bots use this method: **YES**


### MadelineProto Example ([now async for huge speed and parallelism!](https://docs.madelineproto.xyz/docs/ASYNC.html)):


```php
if (!file_exists('madeline.php')) {
    copy('https://phar.madelineproto.xyz/madeline.php', 'madeline.php');
}
include 'madeline.php';

$MadelineProto = new \danog\MadelineProto\API('session.madeline');
$MadelineProto->start();

$messages_Chats = $MadelineProto->messages->getChats(['id' => [InputChat, InputChat], ]);
```

Or, if you're into Lua:

```lua
messages_Chats = messages.getChats({id={InputChat}, })
```

### Errors this method can return:

| Error    | Description   |
|----------|---------------|
|CHAT_ID_INVALID|The provided chat id is invalid|
|PEER_ID_INVALID|The provided peer id is invalid|


