---
title: messages.statedMessageLink
description: Stated message link
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# Constructor: messages.statedMessageLink  
[Back to constructors index](index.md)



Stated message link

### Attributes:

| Name     |    Type       | Required | Description |
|----------|---------------|----------|-------------|
|message|[Message](../types/Message.md) | Optional|Message|
|chats|Array of [Chat](../types/Chat.md) | Yes|Chats|
|users|Array of [User](../types/User.md) | Yes|Users|
|pts|[int](../types/int.md) | Yes|Pts|
|pts\_count|[int](../types/int.md) | Yes|Pts count|
|links|Array of [contacts\_Link](../types/contacts_Link.md) | Yes|Links|
|seq|[int](../types/int.md) | Yes|Seq|



### Type: [messages\_StatedMessage](../types/messages_StatedMessage.md)


### Example:

```php
$messages_statedMessageLink = ['_' => 'messages.statedMessageLink', 'message' => Message, 'chats' => [Chat, Chat], 'users' => [User, User], 'pts' => int, 'pts_count' => int, 'links' => [contacts_Link, contacts_Link], 'seq' => int];
```  


Or, if you're into Lua:

```lua
messages_statedMessageLink={_='messages.statedMessageLink', message=Message, chats={Chat}, users={User}, pts=int, pts_count=int, links={contacts_Link}, seq=int}

```


