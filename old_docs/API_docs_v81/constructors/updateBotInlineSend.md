---
title: updateBotInlineSend
description: Update bot inline send
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# Constructor: updateBotInlineSend  
[Back to constructors index](index.md)



Update bot inline send

### Attributes:

| Name     |    Type       | Required | Description |
|----------|---------------|----------|-------------|
|user\_id|[int](../types/int.md) | Yes|User ID|
|query|[string](../types/string.md) | Yes|Query|
|geo|[GeoPoint](../types/GeoPoint.md) | Optional|Geo|
|id|[string](../types/string.md) | Yes|ID|
|msg\_id|[InputBotInlineMessageID](../types/InputBotInlineMessageID.md) | Optional|Msg ID|



### Type: [Update](../types/Update.md)


### Example:

```php
$updateBotInlineSend = ['_' => 'updateBotInlineSend', 'user_id' => int, 'query' => 'string', 'geo' => GeoPoint, 'id' => 'string', 'msg_id' => InputBotInlineMessageID];
```  


Or, if you're into Lua:

```lua
updateBotInlineSend={_='updateBotInlineSend', user_id=int, query='string', geo=GeoPoint, id='string', msg_id=InputBotInlineMessageID}

```


