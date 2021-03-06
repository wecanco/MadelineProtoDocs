---
title: messages.saveDraft
description: Save a message draft
image: https://docs.madelineproto.xyz/favicons/android-chrome-256x256.png
---
# Method: messages.saveDraft  
[Back to methods index](index.md)


Save a message draft

### Parameters:

| Name     |    Type       | Description | Required |
|----------|---------------|-------------|----------|
|no\_webpage|[Bool](../types/Bool.md) | Disable webpage preview | Optional|
|reply\_to\_msg\_id|[int](../types/int.md) | Reply to message by ID | Optional|
|peer|[Username, chat ID, Update, Message or InputPeer](../types/InputPeer.md) | The chat | Optional|
|message|[string](../types/string.md) | The message | Yes|
|entities|Array of [MessageEntity](../types/MessageEntity.md) | The entities (for styled text) | Optional|
|parse\_mode| [string](../types/string.md) | Whether to parse HTML or Markdown markup in the message| Optional |


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

$Bool = $MadelineProto->messages->saveDraft(['no_webpage' => Bool, 'reply_to_msg_id' => int, 'peer' => InputPeer, 'message' => 'string', 'entities' => [MessageEntity, MessageEntity], 'parse_mode' => 'string', ]);
```

Or, if you're into Lua:

```lua
Bool = messages.saveDraft({no_webpage=Bool, reply_to_msg_id=int, peer=InputPeer, message='string', entities={MessageEntity}, parse_mode='string', })
```


## Return value 

If the length of the provided message is bigger than 4096, the message will be split in chunks and the method will be called multiple times, with the same parameters (except for the message), and an array of [Bool](../types/Bool.md) will be returned instead.



## Usage of parse_mode:

Set parse_mode to html to enable HTML parsing of the message.  

Set parse_mode to Markdown to enable markown AND html parsing of the message.  

The following tags are currently supported:

```html
<br>a newline
<b><i>bold works ok, internal tags are stripped</i> </b>
<strong>bold</strong>
<em>italic</em>
<i>italic</i>
<u>underline</u>
<s>strikethrough</s>
<del>strikethrough</del>
<strike>strikethrough</strike>
<code>inline fixed-width code</code>
<pre>pre-formatted fixed-width code block</pre>
<blockquote>pre-formatted fixed-width code block</blockquote>
<a href="https://github.com">URL</a>
<a href="mention:@danogentili">Mention by username</a>
<a href="mention:186785362">Mention by user id</a>
<pre language="json">Pre tags can have a language attribute</pre>
```

You can also use normal markdown, note that to create mentions you must use the `mention:` syntax like in html:  

```markdown
[Mention by username](mention:@danogentili)
[Mention by user id](mention:186785362)
```

MadelineProto supports all html entities supported by [html_entity_decode](http://php.net/manual/en/function.html-entity-decode.php).
### Errors this method can return:

| Error    | Description   |
|----------|---------------|
|PEER_ID_INVALID|The provided peer id is invalid|


