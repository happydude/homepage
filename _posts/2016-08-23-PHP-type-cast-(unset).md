---
author: Jason Davis
layout: post
title: PHP type cast (unset)
---

<p>I would love to see a use case in php for type casting to (unset)</p>


```php
php > $var = "hello world";
php > var_export((unset) $var);
NULL
php > var_export($var);
'hello world'
```

<p><a href="http://php.net/manual/en/language.types.type-juggling.php">http://php.net/manual/en/language.types.type-juggling.php</a></p>
