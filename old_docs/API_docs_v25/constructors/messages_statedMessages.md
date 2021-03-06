---
title: messages.statedMessages
description: Stated messages
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# Constructor: messages.statedMessages  
[Back to constructors index](index.md)



Stated messages

### Attributes:

| Name     |    Type       | Required | Description |
|----------|---------------|----------|-------------|
|messages|Array of [Message](../types/Message.md) | Yes|Messages|
|chats|Array of [Chat](../types/Chat.md) | Yes|Chats|
|users|Array of [User](../types/User.md) | Yes|Users|
|pts|[int](../types/int.md) | Yes|Pts|
|pts\_count|[int](../types/int.md) | Yes|Pts count|



### Type: [messages\_StatedMessages](../types/messages_StatedMessages.md)


### Example:

```php
$messages_statedMessages = ['_' => 'messages.statedMessages', 'messages' => [Message, Message], 'chats' => [Chat, Chat], 'users' => [User, User], 'pts' => int, 'pts_count' => int];
```  


Or, if you're into Lua:

```lua
messages_statedMessages={_='messages.statedMessages', messages={Message}, chats={Chat}, users={User}, pts=int, pts_count=int}

```


