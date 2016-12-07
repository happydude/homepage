---
layout: post
title: adventures in var_export()ing a resource
---

<p><strong>"Note</strong>:&nbsp;Variables of type&nbsp;<a href="http://php.net/manual/en/language.types.resource.php">resource</a>&nbsp;couldn't be exported by this function." -php.net</p>

<p>Since a resource can’t be exported var_dump() replaces it with null. Good thing to know in those wtf moments.</p>

<p>Ex:</p>

<p>php &gt; $a = fopen('deleteme.php','r');</p>

<p>php &gt; var_export($a);</p>

<p>NULL</p>

<p>php &gt; var_export(is_resource($a));</p>

<p>true</p>

<p>php &gt; var_dump($a);</p>

<p>resource(2) of type (stream)</p>

<p>php &gt;&nbsp;</p>
