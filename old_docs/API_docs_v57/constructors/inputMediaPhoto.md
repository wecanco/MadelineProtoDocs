---
title: inputMediaPhoto
description: Media photo
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# Constructor: inputMediaPhoto  
[Back to constructors index](index.md)



Media photo

### Attributes:

| Name     |    Type       | Required | Description |
|----------|---------------|----------|-------------|
|id|[MessageMedia, Message, Update or InputPhoto](../types/InputPhoto.md) | Optional|ID|
|caption|[string](../types/string.md) | Yes|Caption|



### Type: [InputMedia](../types/InputMedia.md)


### Example:

```php
$inputMediaPhoto = ['_' => 'inputMediaPhoto', 'id' => InputPhoto, 'caption' => 'string'];
```  


Or, if you're into Lua:

```lua
inputMediaPhoto={_='inputMediaPhoto', id=InputPhoto, caption='string'}

```


