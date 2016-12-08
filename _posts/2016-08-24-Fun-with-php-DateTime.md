---
layout: post
title: Fun with php DateTime
---

Create a DateTime


```php
php > $date = new DateTime(null,new DateTimeZone('UTC'));

Set the date to Feburary 30, 2016
php > $date->setDate(2016,2,30);

Check for errors:
php > var_export($date->getLastErrors());
array (
  'warning_count' => 0,
  'warnings' => 
  array (
  ),
  'error_count' => 0,
  'errors' => 
  array (
  ),
)
//The date is set to March 1st:
php > echo $date->format('Y-m-d');
2016-03-01
```


If the invalid date is part of the instantiation a warning is returned in getLastErrors()

```php
php > $date = new DateTime('2016-02-30', new DateTimeZone('UTC'));
php > var_export($date->getLastErrors());
array (
  'warning_count' => 1,
  'warnings' => 
  array (
    11 => 'The parsed date was invalid',
  ),
  'error_count' => 0,
  'errors' => 
  array (
  ),
)
php > echo $date->format('Y-m-d');
2016-03-01
```

