---
title: messages.markDialogUnread
description: Mark dialog as unread 
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# Method: messages.markDialogUnread  
[Back to methods index](index.md)


Mark dialog as unread 

### Parameters:

| Name     |    Type       | Description | Required |
|----------|---------------|-------------|----------|
|unread|[Bool](../types/Bool.md) | Should it be marked or unmarked as read | Optional|
|peer|[Username, chat ID, Update, Message or InputDialogPeer](../types/InputDialogPeer.md) | The dialog to mark as unread | Yes|


### Return type: [Bool](../types/Bool.md)

### Can bots use this method: **NO**


### MadelineProto Example ([now async for huge speed and parallelism!](https://docs.madelineproto.xyz/docs/ASYNC.html)):


```php
if (!file_exists('madeline.php')) {
    copy('https://phar.madelineproto.xyz/madeline.php', 'madeline.php');
}
include 'madeline.php';

$MadelineProto = new \danog\MadelineProto\API('session.madeline');
$MadelineProto->start();

$Bool = $MadelineProto->messages->markDialogUnread(['unread' => Bool, 'peer' => InputDialogPeer, ]);
```

Or, if you're into Lua:

```lua
Bool = messages.markDialogUnread({unread=Bool, peer=InputDialogPeer, })
```

