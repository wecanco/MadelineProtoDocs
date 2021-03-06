---
title: messages.updatePinnedMessage
description: Update pinned message
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# Method: messages.updatePinnedMessage  
[Back to methods index](index.md)


Update pinned message

### Parameters:

| Name     |    Type       | Description | Required |
|----------|---------------|-------------|----------|
|silent|[Bool](../types/Bool.md) | Silent? | Optional|
|peer|[Username, chat ID, Update, Message or InputPeer](../types/InputPeer.md) | Peer | Optional|
|id|[int](../types/int.md) | Message ID | Yes|


### Return type: [Updates](../types/Updates.md)

### Can bots use this method: **YES**


### MadelineProto Example ([now async for huge speed and parallelism!](https://docs.madelineproto.xyz/docs/ASYNC.html)):


```php
if (!file_exists('madeline.php')) {
    copy('https://phar.madelineproto.xyz/madeline.php', 'madeline.php');
}
include 'madeline.php';

$MadelineProto = new \danog\MadelineProto\API('session.madeline');
$MadelineProto->start();

$Updates = $MadelineProto->messages->updatePinnedMessage(['silent' => Bool, 'peer' => InputPeer, 'id' => int, ]);
```

Or, if you're into Lua:

```lua
Updates = messages.updatePinnedMessage({silent=Bool, peer=InputPeer, id=int, })
```

