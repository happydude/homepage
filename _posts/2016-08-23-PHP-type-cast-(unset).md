---
layout: post
title: PHP type cast (unset)
---

<p>I can't really think of a use case but the (unset) cast exists:</p>

<p>php &gt; $var = "hello world";<br />
php &gt; var_export((unset) $var);<br />
NULL<br />
php &gt; var_export($var);<br />
'hello world'</p>

<p>&nbsp;</p>

<p><a href="http://php.net/manual/en/language.types.type-juggling.php">http://php.net/manual/en/language.types.type-juggling.php</a></p>
