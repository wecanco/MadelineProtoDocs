---
title: inputMediaUploadedPhoto
description: Media uploaded photo
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# Constructor: inputMediaUploadedPhoto  
[Back to constructors index](index.md)



Media uploaded photo

### Attributes:

| Name     |    Type       | Required | Description |
|----------|---------------|----------|-------------|
|file|[File path or InputFile](../types/InputFile.md) | Yes|File|
|caption|[string](../types/string.md) | Yes|Caption|



### Type: [InputMedia](../types/InputMedia.md)


### Example:

```php
$inputMediaUploadedPhoto = ['_' => 'inputMediaUploadedPhoto', 'file' => InputFile, 'caption' => 'string'];
```  


Or, if you're into Lua:

```lua
inputMediaUploadedPhoto={_='inputMediaUploadedPhoto', file=InputFile, caption='string'}

```


