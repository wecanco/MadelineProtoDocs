---
title: messages.getDialogs
description: Gets list of chats: you should use $MadelineProto->get_dialogs() instead: https://docs.madelineproto.xyz/docs/DIALOGS.html
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# Method: messages.getDialogs  
[Back to methods index](index.md)


Gets list of chats: you should use $MadelineProto->get_dialogs() instead: https://docs.madelineproto.xyz/docs/DIALOGS.html

### Parameters:

| Name     |    Type       | Description | Required |
|----------|---------------|-------------|----------|
|offset|[int](../types/int.md) | Offset | Yes|
|max\_id|[int](../types/int.md) | Maximum ID of result to return | Yes|
|limit|[int](../types/int.md) | Number of dialogs to fetch | Yes|


### Return type: [messages\_Dialogs](../types/messages_Dialogs.md)

### Can bots use this method: **NO**


### MadelineProto Example ([now async for huge speed and parallelism!](https://docs.madelineproto.xyz/docs/ASYNC.html)):


```php
if (!file_exists('madeline.php')) {
    copy('https://phar.madelineproto.xyz/madeline.php', 'madeline.php');
}
include 'madeline.php';

$MadelineProto = new \danog\MadelineProto\API('session.madeline');
$MadelineProto->start();

$messages_Dialogs = $MadelineProto->messages->getDialogs(['offset' => int, 'max_id' => int, 'limit' => int, ]);
```

Or, if you're into Lua:

```lua
messages_Dialogs = messages.getDialogs({offset=int, max_id=int, limit=int, })
```

### Errors this method can return:

| Error    | Description   |
|----------|---------------|
|INPUT_CONSTRUCTOR_INVALID|The provided constructor is invalid|
|OFFSET_PEER_ID_INVALID|The provided offset peer is invalid|
|SESSION_PASSWORD_NEEDED|2FA is enabled, use a password to login|
|Timeout|Timeout while fetching data|


