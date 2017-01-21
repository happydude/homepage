---
author: Jason Davis
layout: post
title: php (0 === 0.0) is false
---

My derp moment of the week was trying to figure out why 0 === 0 was false. Turns out the value I was testing had been cast elsewhere as a float.
It wasn’t obvious to me initially because when exporting the value php 5.6 was printing 0.
So, even though I was seeing 0, I was comparing a float zero to an int zero.

Testing on [https://3v4l.org/nFQ3O] shows PHP7 will var_export((float) 0) as 0.0. So just another thing to look forward to in PHP7.

```php
<?php
$float = (float) 0;
var_export($float); //php5.x prints 0 while php7 prints 0.0
echo $float; //prints 0 in both versions
var_export($float == 0); //true
var_export($float === 0); //false
var_export($float === 0.0); //true
