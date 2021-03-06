---
title: messages.getEmojiURL
description: Get emoji URL
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# Method: messages.getEmojiURL  
[Back to methods index](index.md)


Get emoji URL

### Parameters:

| Name     |    Type       | Description | Required |
|----------|---------------|-------------|----------|
|lang\_code|[string](../types/string.md) | Language code | Yes|


### Return type: [EmojiURL](../types/EmojiURL.md)

### Can bots use this method: **NO**


### MadelineProto Example ([now async for huge speed and parallelism!](https://docs.madelineproto.xyz/docs/ASYNC.html)):


```php
if (!file_exists('madeline.php')) {
    copy('https://phar.madelineproto.xyz/madeline.php', 'madeline.php');
}
include 'madeline.php';

$MadelineProto = new \danog\MadelineProto\API('session.madeline');
$MadelineProto->start();

$EmojiURL = $MadelineProto->messages->getEmojiURL(['lang_code' => 'string', ]);
```

Or, if you're into Lua:

```lua
EmojiURL = messages.getEmojiURL({lang_code='string', })
```

