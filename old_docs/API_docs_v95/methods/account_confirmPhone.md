---
title: account.confirmPhone
description: Confirm this phone number is associated to this account, obtain phone_code_hash from sendConfirmPhoneCode
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# Method: account.confirmPhone  
[Back to methods index](index.md)


Confirm this phone number is associated to this account, obtain phone_code_hash from sendConfirmPhoneCode

### Parameters:

| Name     |    Type       | Description | Required |
|----------|---------------|-------------|----------|
|phone\_code\_hash|[string](../types/string.md) | Obtain phone_code_hash from sendConfirmPhoneCode | Yes|
|phone\_code|[string](../types/string.md) | The code sent by sendConfirmPhoneCode | Yes|


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

$Bool = $MadelineProto->account->confirmPhone(['phone_code_hash' => 'string', 'phone_code' => 'string', ]);
```

Or, if you're into Lua:

```lua
Bool = account.confirmPhone({phone_code_hash='string', phone_code='string', })
```

### Errors this method can return:

| Error    | Description   |
|----------|---------------|
|CODE_HASH_INVALID|Code hash invalid|
|PHONE_CODE_EMPTY|phone_code is missing|


