---
title: inputEncryptedFile
description: Encrypted file
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# Constructor: inputEncryptedFile  
[Back to constructors index](index.md)



Encrypted file

### Attributes:

| Name     |    Type       | Required | Description |
|----------|---------------|----------|-------------|
|id|[long](../types/long.md) | Yes|ID|
|access\_hash|[long](../types/long.md) | Yes|Access hash|



### Type: [InputEncryptedFile](../types/InputEncryptedFile.md)


### Example:

```php
$inputEncryptedFile = ['_' => 'inputEncryptedFile', 'id' => long, 'access_hash' => long];
```  


Or, if you're into Lua:

```lua
inputEncryptedFile={_='inputEncryptedFile', id=long, access_hash=long}

```


