---
title: phoneCallRequested
description: Phone call requested
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# Constructor: phoneCallRequested  
[Back to constructors index](index.md)



Phone call requested

### Attributes:

| Name     |    Type       | Required | Description |
|----------|---------------|----------|-------------|
|id|[long](../types/long.md) | Yes|ID|
|access\_hash|[long](../types/long.md) | Yes|Access hash|
|date|[int](../types/int.md) | Yes|Date|
|admin\_id|[int](../types/int.md) | Yes|Admin ID|
|participant\_id|[int](../types/int.md) | Yes|Participant ID|
|g\_a\_hash|[bytes](../types/bytes.md) | Yes|G a hash|
|protocol|[PhoneCallProtocol](../types/PhoneCallProtocol.md) | Yes|Protocol|



### Type: [PhoneCall](../types/PhoneCall.md)


### Example:

```php
$phoneCallRequested = ['_' => 'phoneCallRequested', 'id' => long, 'access_hash' => long, 'date' => int, 'admin_id' => int, 'participant_id' => int, 'g_a_hash' => 'bytes', 'protocol' => PhoneCallProtocol];
```  


Or, if you're into Lua:

```lua
phoneCallRequested={_='phoneCallRequested', id=long, access_hash=long, date=int, admin_id=int, participant_id=int, g_a_hash='bytes', protocol=PhoneCallProtocol}

```


