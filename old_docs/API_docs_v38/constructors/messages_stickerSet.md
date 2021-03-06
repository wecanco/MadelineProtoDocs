---
title: messages.stickerSet
description: Sticker set
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# Constructor: messages.stickerSet  
[Back to constructors index](index.md)



Sticker set

### Attributes:

| Name     |    Type       | Required | Description |
|----------|---------------|----------|-------------|
|set|[StickerSet](../types/StickerSet.md) | Yes|Set|
|packs|Array of [StickerPack](../types/StickerPack.md) | Yes|Packs|
|documents|Array of [Document](../types/Document.md) | Yes|Documents|



### Type: [messages\_StickerSet](../types/messages_StickerSet.md)


### Example:

```php
$messages_stickerSet = ['_' => 'messages.stickerSet', 'set' => StickerSet, 'packs' => [StickerPack, StickerPack], 'documents' => [Document, Document]];
```  


Or, if you're into Lua:

```lua
messages_stickerSet={_='messages.stickerSet', set=StickerSet, packs={StickerPack}, documents={Document}}

```


