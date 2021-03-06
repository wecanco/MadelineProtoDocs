---
title: messages.requestUrlAuth
description: Request URL authorization
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# Method: messages.requestUrlAuth  
[Back to methods index](index.md)


Request URL authorization

### Parameters:

| Name     |    Type       | Description | Required |
|----------|---------------|-------------|----------|
|peer|[Username, chat ID, Update, Message or InputPeer](../types/InputPeer.md) | Peer | Optional|
|msg\_id|[int](../types/int.md) | Message ID | Yes|
|button\_id|[int](../types/int.md) | Button ID | Yes|


### Return type: [UrlAuthResult](../types/UrlAuthResult.md)

### Can bots use this method: **NO**


### MadelineProto Example ([now async for huge speed and parallelism!](https://docs.madelineproto.xyz/docs/ASYNC.html)):


```php
if (!file_exists('madeline.php')) {
    copy('https://phar.madelineproto.xyz/madeline.php', 'madeline.php');
}
include 'madeline.php';

$MadelineProto = new \danog\MadelineProto\API('session.madeline');
$MadelineProto->start();

$UrlAuthResult = $MadelineProto->messages->requestUrlAuth(['peer' => InputPeer, 'msg_id' => int, 'button_id' => int, ]);
```

Or, if you're into Lua:

```lua
UrlAuthResult = messages.requestUrlAuth({peer=InputPeer, msg_id=int, button_id=int, })
```

