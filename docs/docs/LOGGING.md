---
title: Logging
description: MadelineProto provides a unified class for logging messages to the logging destination defined in [settings](SETTINGS.html#settingslogger).  
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# Logging

MadelineProto provides a unified class for logging messages to the logging destination defined in [settings](SETTINGS.html#settingslogger).  

Use the [settings](SETTINGS.html#settingslogger) to modify the default logging destination and log verbosity.  

Note: when running from web, MadelineProto will also automatically enable logging of **PHP errors** (not MadelineProto logs) to `MadelineProto.log`, located in the same directory as the script that loaded MadelineProto.  


```php
$MadelineProto->logger($message, $level);
```

`$message` is a string, an integer, an array, or any json-encodable object.  
`$level` (optional) is one of the following constants:
* `\danog\MadelineProto\Logger::FATAL_ERROR` - Indicates a fatal error
* `\danog\MadelineProto\Logger::ERROR` - Indicates a recoverable error
* `\danog\MadelineProto\Logger::NOTICE` - Indicates an info message
* `\danog\MadelineProto\Logger::VERBOSE` - Indicates a verbose info message
* `\danog\MadelineProto\Logger::ULTRA_VERBOSE` - Indicates an ultra verbose


By default, `$level` is `\danog\MadelineProto\Logger::NOTICE`.

<a href="https://docs.madelineproto.xyz/docs/CALLS.html">Next section</a>