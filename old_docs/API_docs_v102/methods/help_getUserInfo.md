---
title: help.getUserInfo
description: Get user info
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# Method: help.getUserInfo  
[Back to methods index](index.md)


Get user info

### Parameters:

| Name     |    Type       | Description | Required |
|----------|---------------|-------------|----------|
|user\_id|[Username, chat ID, Update, Message or InputUser](../types/InputUser.md) | User ID | Optional|


### Return type: [help\_UserInfo](../types/help_UserInfo.md)

### Can bots use this method: **NO**


### MadelineProto Example ([now async for huge speed and parallelism!](https://docs.madelineproto.xyz/docs/ASYNC.html)):


```php
if (!file_exists('madeline.php')) {
    copy('https://phar.madelineproto.xyz/madeline.php', 'madeline.php');
}
include 'madeline.php';

$MadelineProto = new \danog\MadelineProto\API('session.madeline');
$MadelineProto->start();

$help_UserInfo = $MadelineProto->help->getUserInfo(['user_id' => InputUser, ]);
```

Or, if you're into Lua:

```lua
help_UserInfo = help.getUserInfo({user_id=InputUser, })
```

