---
author: Jason Davis
layout: post
title: var_export does not handle circular references
modified: 2020-03-04T17:13:00-07:00
---

This error happens when trying to var_export() an object that references another object that references back to the exported object.

For example Object A that references Object B when Object B references Object A.

A simple demo using php7
```php
php > $a = new StdClass();
php > $b = new StdClass();
php > $a->objB = $b;
php > $b->objA = $a;
php > var_export($a);
PHP Warning:  var_export does not handle circular references in php shell code on line 1
stdClass::__set_state(array(
   'objB' =>
  stdClass::__set_state(array(
     'objA' => NULL,
  )),
))

```

Using var_export on objects with recursive dependencies got demoted from a fatal to a warning somewhere between php 5.3 and 5.5

php 5.3
```bash
PHP Fatal error:  Nesting level too deep - recursive dependency?
 'type’ => 1,
 'message’ => ‘Nesting level too deep - recursive dependency?’,
```


php 5.5
```bash
Warning: var_export does not handle circular references 
 'type’ => 2,
 'message’ => 'var_export does not handle circular references’,
```

My fallback option is var_dump(). var_dump() displays circular references as `*RECURSION*` rather than issuing a warning (or a Fatal in 5.3).

```php
php > var_dump($a);
object(stdClass)#1 (1) {
  ["objB"]=>
  object(stdClass)#2 (1) {
    ["objA"]=>
    *RECURSION*
  }
}

```