---
title: secureValueErrorTranslationFile
description: Secure value error translation file
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# Constructor: secureValueErrorTranslationFile  
[Back to constructors index](index.md)



Secure value error translation file

### Attributes:

| Name     |    Type       | Required | Description |
|----------|---------------|----------|-------------|
|type|[SecureValueType](../types/SecureValueType.md) | Yes|Type|
|file\_hash|[bytes](../types/bytes.md) | Yes|File hash|
|text|[string](../types/string.md) | Yes|Text|



### Type: [SecureValueError](../types/SecureValueError.md)


### Example:

```php
$secureValueErrorTranslationFile = ['_' => 'secureValueErrorTranslationFile', 'type' => SecureValueType, 'file_hash' => 'bytes', 'text' => 'string'];
```  


Or, if you're into Lua:

```lua
secureValueErrorTranslationFile={_='secureValueErrorTranslationFile', type=SecureValueType, file_hash='bytes', text='string'}

```


