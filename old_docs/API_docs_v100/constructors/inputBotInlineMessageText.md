---
title: inputBotInlineMessageText
description: Bot inline message text
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# Constructor: inputBotInlineMessageText  
[Back to constructors index](index.md)



Bot inline message text

### Attributes:

| Name     |    Type       | Required | Description |
|----------|---------------|----------|-------------|
|no\_webpage|[Bool](../types/Bool.md) | Optional|No webpage?|
|message|[string](../types/string.md) | Yes|Message|
|entities|Array of [MessageEntity](../types/MessageEntity.md) | Optional|Entities|
|reply\_markup|[ReplyMarkup](../types/ReplyMarkup.md) | Optional|Reply markup|



### Type: [InputBotInlineMessage](../types/InputBotInlineMessage.md)


### Example:

```php
$inputBotInlineMessageText = ['_' => 'inputBotInlineMessageText', 'no_webpage' => Bool, 'message' => 'string', 'entities' => [MessageEntity, MessageEntity], 'reply_markup' => ReplyMarkup];
```  


Or, if you're into Lua:

```lua
inputBotInlineMessageText={_='inputBotInlineMessageText', no_webpage=Bool, message='string', entities={MessageEntity}, reply_markup=ReplyMarkup}

```



## Usage of reply_markup

You can provide bot API reply_markup objects here.  


