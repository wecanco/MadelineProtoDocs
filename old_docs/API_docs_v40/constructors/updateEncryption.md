---
title: updateEncryption
description: Update encryption
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# Constructor: updateEncryption  
[Back to constructors index](index.md)



Update encryption

### Attributes:

| Name     |    Type       | Required | Description |
|----------|---------------|----------|-------------|
|chat|[EncryptedChat](../types/EncryptedChat.md) | Optional|Chat|
|date|[int](../types/int.md) | Yes|Date|



### Type: [Update](../types/Update.md)


### Example:

```php
$updateEncryption = ['_' => 'updateEncryption', 'chat' => EncryptedChat, 'date' => int];
```  


Or, if you're into Lua:

```lua
updateEncryption={_='updateEncryption', chat=EncryptedChat, date=int}

```


