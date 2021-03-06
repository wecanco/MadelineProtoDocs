---
title: messages.getEmojiKeywordsLanguages
description: Get emoji keyword languages
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# Method: messages.getEmojiKeywordsLanguages  
[Back to methods index](index.md)


Get emoji keyword languages

### Parameters:

| Name     |    Type       | Description | Required |
|----------|---------------|-------------|----------|
|lang\_codes|Array of [string](../types/string.md) | Language codes | Yes|


### Return type: [Vector\_of\_EmojiLanguage](../types/EmojiLanguage.md)

### Can bots use this method: **YES**


### MadelineProto Example ([now async for huge speed and parallelism!](https://docs.madelineproto.xyz/docs/ASYNC.html)):


```php
if (!file_exists('madeline.php')) {
    copy('https://phar.madelineproto.xyz/madeline.php', 'madeline.php');
}
include 'madeline.php';

$MadelineProto = new \danog\MadelineProto\API('session.madeline');
$MadelineProto->start();

$Vector_of_EmojiLanguage = $MadelineProto->messages->getEmojiKeywordsLanguages(['lang_codes' => ['string', 'string'], ]);
```

Or, if you're into Lua:

```lua
Vector_of_EmojiLanguage = messages.getEmojiKeywordsLanguages({lang_codes={'string'}, })
```

