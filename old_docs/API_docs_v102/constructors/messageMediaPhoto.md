---
title: messageMediaPhoto
description: Message media photo
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# Constructor: messageMediaPhoto  
[Back to constructors index](index.md)



Message media photo

### Attributes:

| Name     |    Type       | Required | Description |
|----------|---------------|----------|-------------|
|photo|[Photo](../types/Photo.md) | Optional|Photo|
|ttl\_seconds|[int](../types/int.md) | Optional|Ttl seconds|



### Type: [MessageMedia](../types/MessageMedia.md)


### Example:

```php
$messageMediaPhoto = ['_' => 'messageMediaPhoto', 'photo' => Photo, 'ttl_seconds' => int];
```  


Or, if you're into Lua:

```lua
messageMediaPhoto={_='messageMediaPhoto', photo=Photo, ttl_seconds=int}

```


