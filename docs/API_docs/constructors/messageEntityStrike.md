---
title: messageEntityStrike
description: Strikethrough
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# Constructor: messageEntityStrike  
[Back to constructors index](index.md)



Strikethrough

### Attributes:

| Name     |    Type       | Required | Description |
|----------|---------------|----------|-------------|
|offset|[int](../types/int.md) | Yes|Offset|
|length|[int](../types/int.md) | Yes|Length|



### Type: [MessageEntity](../types/MessageEntity.md)


### Example:

```php
$messageEntityStrike = ['_' => 'messageEntityStrike', 'offset' => int, 'length' => int];
```  


Or, if you're into Lua:

```lua
messageEntityStrike={_='messageEntityStrike', offset=int, length=int}

```


