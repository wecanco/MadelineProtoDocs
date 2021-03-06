---
title: channelFull
description: Full channel
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# Constructor: channelFull  
[Back to constructors index](index.md)



Full channel

### Attributes:

| Name     |    Type       | Required | Description |
|----------|---------------|----------|-------------|
|id|[int](../types/int.md) | Yes|ID|
|about|[string](../types/string.md) | Yes|About|
|participants\_count|[int](../types/int.md) | Optional|Participants count|
|admins\_count|[int](../types/int.md) | Optional|Admins count|
|kicked\_count|[int](../types/int.md) | Optional|Kicked count|
|read\_inbox\_max\_id|[int](../types/int.md) | Yes|Read inbox max ID|
|unread\_count|[int](../types/int.md) | Yes|Unread count|
|unread\_important\_count|[int](../types/int.md) | Yes|Unread important count|
|chat\_photo|[Photo](../types/Photo.md) | Optional|Chat photo|
|notify\_settings|[PeerNotifySettings](../types/PeerNotifySettings.md) | Optional|Notify settings|
|exported\_invite|[ExportedChatInvite](../types/ExportedChatInvite.md) | Yes|Exported invite|



### Type: [ChatFull](../types/ChatFull.md)


### Example:

```php
$channelFull = ['_' => 'channelFull', 'id' => int, 'about' => 'string', 'participants_count' => int, 'admins_count' => int, 'kicked_count' => int, 'read_inbox_max_id' => int, 'unread_count' => int, 'unread_important_count' => int, 'chat_photo' => Photo, 'notify_settings' => PeerNotifySettings, 'exported_invite' => ExportedChatInvite];
```  


Or, if you're into Lua:

```lua
channelFull={_='channelFull', id=int, about='string', participants_count=int, admins_count=int, kicked_count=int, read_inbox_max_id=int, unread_count=int, unread_important_count=int, chat_photo=Photo, notify_settings=PeerNotifySettings, exported_invite=ExportedChatInvite}

```


