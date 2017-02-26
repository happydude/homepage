---
author: Jason Davis
layout: post
title: Fun with php DateTime
modified: 2017-02-26T14:00:00-07:00
---

Create a DateTime object

```php
php > $date = new DateTime(null,new DateTimeZone('UTC'));
```
Set the date to Feburary 30, 2016
```php
php > $date->setDate(2016,2,30);
```
No errors or warnings when checking for errors:
```php
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
```
Feburary 30th is changed to March 1st:
```php
php > echo $date->format('Y-m-d');
2016-03-01
```

If an invalid date is used as a parameter during instatiation a warning is returned in getLastErrors()

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
```
The end result is still the same adjusted date.
```php
php > echo $date->format('Y-m-d');
2016-03-01
```

