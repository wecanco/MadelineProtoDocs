---
title: messages.getAttachedStickers
description: Get stickers attachable to images
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# Method: messages.getAttachedStickers  
[Back to methods index](index.md)


Get stickers attachable to images

### Parameters:

| Name     |    Type       | Description | Required |
|----------|---------------|-------------|----------|
|media|[InputStickeredMedia](../types/InputStickeredMedia.md) | The stickered media | Yes|


### Return type: [Vector\_of\_StickerSetCovered](../types/StickerSetCovered.md)

### Can bots use this method: **NO**


### MadelineProto Example ([now async for huge speed and parallelism!](https://docs.madelineproto.xyz/docs/ASYNC.html)):


```php
if (!file_exists('madeline.php')) {
    copy('https://phar.madelineproto.xyz/madeline.php', 'madeline.php');
}
include 'madeline.php';

$MadelineProto = new \danog\MadelineProto\API('session.madeline');
$MadelineProto->start();

$Vector_of_StickerSetCovered = $MadelineProto->messages->getAttachedStickers(['media' => InputStickeredMedia, ]);
```

Or, if you're into Lua:

```lua
Vector_of_StickerSetCovered = messages.getAttachedStickers({media=InputStickeredMedia, })
```

