---
title: inputMediaDocument
description: Media document
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# Constructor: inputMediaDocument  
[Back to constructors index](index.md)



Media document

### Attributes:

| Name     |    Type       | Required | Description |
|----------|---------------|----------|-------------|
|id|[MessageMedia, Message, Update or InputDocument](../types/InputDocument.md) | Optional|ID|
|ttl\_seconds|[int](../types/int.md) | Optional|Ttl seconds|



### Type: [InputMedia](../types/InputMedia.md)


### Example:

```php
$inputMediaDocument = ['_' => 'inputMediaDocument', 'id' => InputDocument, 'ttl_seconds' => int];
```  


Or, if you're into Lua:

```lua
inputMediaDocument={_='inputMediaDocument', id=InputDocument, ttl_seconds=int}

```


