---
title: messages.statedMessage
description: Stated message
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# Constructor: messages.statedMessage  
[Back to constructors index](index.md)



Stated message

### Attributes:

| Name     |    Type       | Required | Description |
|----------|---------------|----------|-------------|
|message|[Message](../types/Message.md) | Optional|Message|
|chats|Array of [Chat](../types/Chat.md) | Yes|Chats|
|users|Array of [User](../types/User.md) | Yes|Users|
|pts|[int](../types/int.md) | Yes|Pts|
|pts\_count|[int](../types/int.md) | Yes|Pts count|



### Type: [messages\_StatedMessage](../types/messages_StatedMessage.md)


### Example:

```php
$messages_statedMessage = ['_' => 'messages.statedMessage', 'message' => Message, 'chats' => [Chat, Chat], 'users' => [User, User], 'pts' => int, 'pts_count' => int];
```  


Or, if you're into Lua:

```lua
messages_statedMessage={_='messages.statedMessage', message=Message, chats={Chat}, users={User}, pts=int, pts_count=int}

```


