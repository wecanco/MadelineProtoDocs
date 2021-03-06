---
title: messages.addChatUser
description: Add a user to a normal chat (use channels->inviteToChannel for supergroups)
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# Method: messages.addChatUser  
[Back to methods index](index.md)


Add a user to a normal chat (use channels->inviteToChannel for supergroups)

### Parameters:

| Name     |    Type       | Description | Required |
|----------|---------------|-------------|----------|
|chat\_id|[Username, chat ID, Update, Message or InputPeer](../types/InputPeer.md) | The chat where to invite users | Optional|
|user\_id|[Username, chat ID, Update, Message or InputUser](../types/InputUser.md) | The user to invite | Optional|
|fwd\_limit|[int](../types/int.md) | Number of old messages the user will see | Yes|


### Return type: [messages\_StatedMessage](../types/messages_StatedMessage.md)

### Can bots use this method: **NO**


### MadelineProto Example ([now async for huge speed and parallelism!](https://docs.madelineproto.xyz/docs/ASYNC.html)):


```php
if (!file_exists('madeline.php')) {
    copy('https://phar.madelineproto.xyz/madeline.php', 'madeline.php');
}
include 'madeline.php';

$MadelineProto = new \danog\MadelineProto\API('session.madeline');
$MadelineProto->start();

$messages_StatedMessage = $MadelineProto->messages->addChatUser(['chat_id' => InputPeer, 'user_id' => InputUser, 'fwd_limit' => int, ]);
```

Or, if you're into Lua:

```lua
messages_StatedMessage = messages.addChatUser({chat_id=InputPeer, user_id=InputUser, fwd_limit=int, })
```

### Errors this method can return:

| Error    | Description   |
|----------|---------------|
|CHAT_ADMIN_REQUIRED|You must be an admin in this chat to do this|
|CHAT_ID_INVALID|The provided chat id is invalid|
|INPUT_USER_DEACTIVATED|The specified user was deleted|
|PEER_ID_INVALID|The provided peer id is invalid|
|USER_ALREADY_PARTICIPANT|The user is already in the group|
|USER_ID_INVALID|The provided user ID is invalid|
|USERS_TOO_MUCH|The maximum number of users has been exceeded (to create a chat, for example)|
|USER_NOT_MUTUAL_CONTACT|The provided user is not a mutual contact|
|USER_PRIVACY_RESTRICTED|The user's privacy settings do not allow you to do this|


