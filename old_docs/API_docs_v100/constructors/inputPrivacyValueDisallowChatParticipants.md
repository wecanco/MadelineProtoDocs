---
title: inputPrivacyValueDisallowChatParticipants
description: Disallowed chats
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# Constructor: inputPrivacyValueDisallowChatParticipants  
[Back to constructors index](index.md)



Disallowed chats

### Attributes:

| Name     |    Type       | Required | Description |
|----------|---------------|----------|-------------|
|chats|Array of [int](../types/int.md) | Yes|CHats|



### Type: [InputPrivacyRule](../types/InputPrivacyRule.md)


### Example:

```php
$inputPrivacyValueDisallowChatParticipants = ['_' => 'inputPrivacyValueDisallowChatParticipants', 'chats' => [int, int]];
```  


Or, if you're into Lua:

```lua
inputPrivacyValueDisallowChatParticipants={_='inputPrivacyValueDisallowChatParticipants', chats={int}}

```


