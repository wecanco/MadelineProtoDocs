---
title: help.getTermsOfServiceUpdate
description: Get updated TOS
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# Method: help.getTermsOfServiceUpdate  
[Back to methods index](index.md)


Get updated TOS



### Return type: [help\_TermsOfServiceUpdate](../types/help_TermsOfServiceUpdate.md)

### Can bots use this method: **NO**


### MadelineProto Example ([now async for huge speed and parallelism!](https://docs.madelineproto.xyz/docs/ASYNC.html)):


```php
if (!file_exists('madeline.php')) {
    copy('https://phar.madelineproto.xyz/madeline.php', 'madeline.php');
}
include 'madeline.php';

$MadelineProto = new \danog\MadelineProto\API('session.madeline');
$MadelineProto->start();

$help_TermsOfServiceUpdate = $MadelineProto->help->getTermsOfServiceUpdate();
```

Or, if you're into Lua:

```lua
help_TermsOfServiceUpdate = help.getTermsOfServiceUpdate({})
```

