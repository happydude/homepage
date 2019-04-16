---
author: Jason Davis
layout: post
title: PHP http streams default to HTTP/1.0
---

Today I learned the php fopen wrapper for http streams defaults to http 1.0. ☹

Thankfully you can change this default.

```php
<?php
$context = stream_context_create(['http' =>
    [
        'method' => 'GET',
        'header' => [
            'Accept: */*',
        ],
        'protocol_version' => 1.1
    ]
]);

$xml = simplexml_load_string(
    file_get_contents('https://xmlstuff.example.net/cgi-mod/stats.cgi', false, $context)
);
var_export($xml);
```

References:
---
1. <https://www.php.net/manual/en/function.stream-context-create.php>
2. <https://www.php.net/manual/en/function.file-get-contents.php>
3. <https://www.php.net/manual/en/context.http.php>
