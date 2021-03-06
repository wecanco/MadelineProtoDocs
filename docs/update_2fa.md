---
title: update_2fa
description: Update 2FA password
---
## Method: update_2fa  

The params array can contain password (current password), new_password, email (optional) and hint params.

### Parameters:

| Name     |    Type       |
|----------|---------------|
|params|An array of parameters|

### Return type: [Bool](API_docs/types/Bool.md)

### Example ([now fully async!](https://docs.madelineproto.xyz/docs/ASYNC.html)):


```php
try {
    $MadelineProto->update_2fa(['password' => 'current password', 'new_password' => 'New password', 'email' => 'daniil@daniil.it', 'hint' => 'ponies']);
} catch (RPCErrorException $e) {
    if (strpos($e->rpc, 'EMAIL_UNCONFIRMED_') !== false) {
        $Bool = yield $MadelineProto->account->confirmPasswordEmail(['code' => yield $MadelineProto->readline('Enter your email code: ')]);
    } else {
        throw $e;
    }
}
```
