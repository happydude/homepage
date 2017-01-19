---
author: Jason Davis
layout: post
title: adventures in var_export()ing a resource
---

<p><strong>"Note</strong>:&nbsp;Variables of type&nbsp;<a href="http://php.net/manual/en/language.types.resource.php">resource</a>&nbsp;couldn't be exported by this function." -php.net</p>

<p>Since a resource can’t be exported var_dump() replaces it with null. Good thing to know in those wtf moments.</p>

```php
php > $a = fopen('deleteme.php','r');

php > var_export($a);

NULL

php > var_export(is_resource($a));

true

php > var_dump($a);

resource(2) of type (stream)

php > 
```
