---
title: photos.uploadProfilePhoto
description: Upload profile photo
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# Method: photos.uploadProfilePhoto  
[Back to methods index](index.md)


Upload profile photo

### Parameters:

| Name     |    Type       | Description | Required |
|----------|---------------|-------------|----------|
|file|[File path or InputFile](../types/InputFile.md) | The photo | Yes|


### Return type: [photos\_Photo](../types/photos_Photo.md)

### Can bots use this method: **NO**


### MadelineProto Example ([now async for huge speed and parallelism!](https://docs.madelineproto.xyz/docs/ASYNC.html)):


```php
if (!file_exists('madeline.php')) {
    copy('https://phar.madelineproto.xyz/madeline.php', 'madeline.php');
}
include 'madeline.php';

$MadelineProto = new \danog\MadelineProto\API('session.madeline');
$MadelineProto->start();

$photos_Photo = $MadelineProto->photos->uploadProfilePhoto(['file' => InputFile, ]);
```

Or, if you're into Lua:

```lua
photos_Photo = photos.uploadProfilePhoto({file=InputFile, })
```

### Errors this method can return:

| Error    | Description   |
|----------|---------------|
|FILE_PARTS_INVALID|The number of file parts is invalid|
|IMAGE_PROCESS_FAILED|Failure while processing image|
|PHOTO_CROP_SIZE_SMALL|Photo is too small|
|PHOTO_EXT_INVALID|The extension of the photo is invalid|


