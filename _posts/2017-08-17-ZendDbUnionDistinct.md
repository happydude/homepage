---
author: Jason Davis
layout: post
title: Zend\Db UNION DISTINCT
---
Need a UNION DISTINCT in Zend\Db?
=======================
It isn't all that difficult, since it took me a while to figure out:
```php
<?php
$select1 = new \Zend\Db\Sql\Select();
$select2 = new \Zend\Db\Sql\Select();

$select2->combine($select1,\Zend\Db\Sql\Select::COMBINE_UNION, 'distinct');

var_export($select2->getSqlString());
```

```
'( SELECT * ) UNION DISTINCT ( SELECT * )'
```
