---
title: user
description: User
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# Constructor: user  
[Back to constructors index](index.md)



User

### Attributes:

| Name     |    Type       | Required | Description |
|----------|---------------|----------|-------------|
|self|[Bool](../types/Bool.md) | Optional|Self?|
|contact|[Bool](../types/Bool.md) | Optional|Contact?|
|mutual\_contact|[Bool](../types/Bool.md) | Optional|Mutual contact?|
|deleted|[Bool](../types/Bool.md) | Optional|Deleted?|
|bot|[Bool](../types/Bool.md) | Optional|Bot?|
|bot\_chat\_history|[Bool](../types/Bool.md) | Optional|Bot chat history?|
|bot\_nochats|[Bool](../types/Bool.md) | Optional|Bot nochats?|
|verified|[Bool](../types/Bool.md) | Optional|Verified?|
|restricted|[Bool](../types/Bool.md) | Optional|Restricted?|
|min|[Bool](../types/Bool.md) | Optional|Min?|
|bot\_inline\_geo|[Bool](../types/Bool.md) | Optional|Bot inline geo?|
|id|[int](../types/int.md) | Yes|ID|
|access\_hash|[long](../types/long.md) | Optional|Access hash|
|first\_name|[string](../types/string.md) | Optional|First name|
|last\_name|[string](../types/string.md) | Optional|Last name|
|username|[string](../types/string.md) | Optional|Username|
|phone|[string](../types/string.md) | Optional|Phone|
|photo|[UserProfilePhoto](../types/UserProfilePhoto.md) | Optional|Photo|
|status|[UserStatus](../types/UserStatus.md) | Optional|Status|
|bot\_info\_version|[int](../types/int.md) | Optional|Bot info version|
|restriction\_reason|[string](../types/string.md) | Optional|Restriction reason|
|bot\_inline\_placeholder|[string](../types/string.md) | Optional|Bot inline placeholder|



### Type: [User](../types/User.md)


### Example:

```php
$user = ['_' => 'user', 'self' => Bool, 'contact' => Bool, 'mutual_contact' => Bool, 'deleted' => Bool, 'bot' => Bool, 'bot_chat_history' => Bool, 'bot_nochats' => Bool, 'verified' => Bool, 'restricted' => Bool, 'min' => Bool, 'bot_inline_geo' => Bool, 'id' => int, 'access_hash' => long, 'first_name' => 'string', 'last_name' => 'string', 'username' => 'string', 'phone' => 'string', 'photo' => UserProfilePhoto, 'status' => UserStatus, 'bot_info_version' => int, 'restriction_reason' => 'string', 'bot_inline_placeholder' => 'string'];
```  


Or, if you're into Lua:

```lua
user={_='user', self=Bool, contact=Bool, mutual_contact=Bool, deleted=Bool, bot=Bool, bot_chat_history=Bool, bot_nochats=Bool, verified=Bool, restricted=Bool, min=Bool, bot_inline_geo=Bool, id=int, access_hash=long, first_name='string', last_name='string', username='string', phone='string', photo=UserProfilePhoto, status=UserStatus, bot_info_version=int, restriction_reason='string', bot_inline_placeholder='string'}

```


