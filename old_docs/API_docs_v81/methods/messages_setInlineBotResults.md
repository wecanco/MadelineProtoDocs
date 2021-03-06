---
title: messages.setInlineBotResults
description: Bots only: set the results of an inline query
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# Method: messages.setInlineBotResults  
[Back to methods index](index.md)


Bots only: set the results of an inline query

### Parameters:

| Name     |    Type       | Description | Required |
|----------|---------------|-------------|----------|
|gallery|[Bool](../types/Bool.md) | Is this a gallery? | Optional|
|private|[Bool](../types/Bool.md) | Is this result private (not cached)? | Optional|
|query\_id|[long](../types/long.md) | Query ID | Yes|
|results|Array of [InputBotInlineResult](../types/InputBotInlineResult.md) | Results | Yes|
|cache\_time|[int](../types/int.md) | Cache time | Yes|
|next\_offset|[string](../types/string.md) | The next offset | Optional|
|switch\_pm|[InlineBotSwitchPM](../types/InlineBotSwitchPM.md) | Switch to PM? | Optional|


### Return type: [Bool](../types/Bool.md)

### Can bots use this method: **YES**


### MadelineProto Example ([now async for huge speed and parallelism!](https://docs.madelineproto.xyz/docs/ASYNC.html)):


```php
if (!file_exists('madeline.php')) {
    copy('https://phar.madelineproto.xyz/madeline.php', 'madeline.php');
}
include 'madeline.php';

$MadelineProto = new \danog\MadelineProto\API('session.madeline');
$MadelineProto->start();

$Bool = $MadelineProto->messages->setInlineBotResults(['gallery' => Bool, 'private' => Bool, 'query_id' => long, 'results' => [InputBotInlineResult, InputBotInlineResult], 'cache_time' => int, 'next_offset' => 'string', 'switch_pm' => InlineBotSwitchPM, ]);
```

Or, if you're into Lua:

```lua
Bool = messages.setInlineBotResults({gallery=Bool, private=Bool, query_id=long, results={InputBotInlineResult}, cache_time=int, next_offset='string', switch_pm=InlineBotSwitchPM, })
```

### Errors this method can return:

| Error    | Description   |
|----------|---------------|
|ARTICLE_TITLE_EMPTY|The title of the article is empty|
|BUTTON_DATA_INVALID|The provided button data is invalid|
|BUTTON_TYPE_INVALID|The type of one of the buttons you provided is invalid|
|BUTTON_URL_INVALID|Button URL invalid|
|MESSAGE_EMPTY|The provided message is empty|
|QUERY_ID_INVALID|The query ID is invalid|
|REPLY_MARKUP_INVALID|The provided reply markup is invalid|
|RESULT_TYPE_INVALID|Result type invalid|
|SEND_MESSAGE_TYPE_INVALID|The message type is invalid|
|START_PARAM_INVALID|Start parameter invalid|
|USER_BOT_INVALID|This method can only be called by a bot|


