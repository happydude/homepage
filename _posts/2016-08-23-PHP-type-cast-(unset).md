---
author: Jason Davis
layout: post
title: PHP type cast (unset)
modified: 2017-07-13T22:09:00-07:00
---

<p>I would love to see a use case in php for type casting to (unset)</p>
<p>Update:2017-07-13 This seems to confirm there is no use for (unset) since it is slated for deprecation in 7.2  🙂</p>
<p>
<a href="https://wiki.php.net/rfc/deprecations_php_7_2#unset_cast">https://wiki.php.net/rfc/deprecations_php_7_2#unset_cast</a>
</p>

```php
php > $var = "hello world";
php > var_export((unset) $var);
NULL
php > var_export($var);
'hello world'
```

<p><a href="http://php.net/manual/en/language.types.type-juggling.php">http://php.net/manual/en/language.types.type-juggling.php</a></p>
