---
title: channelMessagesFilter
description: Channel messages filter
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# Constructor: channelMessagesFilter  
[Back to constructors index](index.md)



Channel messages filter

### Attributes:

| Name     |    Type       | Required | Description |
|----------|---------------|----------|-------------|
|ranges|Array of [MessageRange](../types/MessageRange.md) | Yes|Ranges|



### Type: [ChannelMessagesFilter](../types/ChannelMessagesFilter.md)


### Example:

```php
$channelMessagesFilter = ['_' => 'channelMessagesFilter', 'ranges' => [MessageRange, MessageRange]];
```  


Or, if you're into Lua:

```lua
channelMessagesFilter={_='channelMessagesFilter', ranges={MessageRange}}

```


