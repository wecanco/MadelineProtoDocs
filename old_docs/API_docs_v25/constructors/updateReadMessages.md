---
title: updateReadMessages
description: Update read messages
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# Constructor: updateReadMessages  
[Back to constructors index](index.md)



Update read messages

### Attributes:

| Name     |    Type       | Required | Description |
|----------|---------------|----------|-------------|
|messages|Array of [int](../types/int.md) | Yes|Messages|
|pts|[int](../types/int.md) | Yes|Pts|
|pts\_count|[int](../types/int.md) | Yes|Pts count|



### Type: [Update](../types/Update.md)


### Example:

```php
$updateReadMessages = ['_' => 'updateReadMessages', 'messages' => [int, int], 'pts' => int, 'pts_count' => int];
```  


Or, if you're into Lua:

```lua
updateReadMessages={_='updateReadMessages', messages={int}, pts=int, pts_count=int}

```


