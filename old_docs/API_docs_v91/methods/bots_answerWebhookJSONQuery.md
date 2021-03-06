---
title: bots.answerWebhookJSONQuery
description: Send webhook request via bot API
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# Method: bots.answerWebhookJSONQuery  
[Back to methods index](index.md)


Send webhook request via bot API

### Parameters:

| Name     |    Type       | Description | Required |
|----------|---------------|-------------|----------|
|query\_id|[long](../types/long.md) | The query ID | Yes|
|data|[DataJSON](../types/DataJSON.md) | The parameters | Yes|


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

$Bool = $MadelineProto->bots->answerWebhookJSONQuery(['query_id' => long, 'data' => DataJSON, ]);
```

Or, if you're into Lua:

```lua
Bool = bots.answerWebhookJSONQuery({query_id=long, data=DataJSON, })
```

### Errors this method can return:

| Error    | Description   |
|----------|---------------|
|QUERY_ID_INVALID|The query ID is invalid|
|USER_BOT_INVALID|This method can only be called by a bot|


