---
layout: post
title: Fun with php DateTime
---

<p>Create a DateTime</p>

<p>php &gt; $date = new DateTime(null,new DateTimeZone('UTC'));</p>

<p>Set the date to Feburary 30, 2016<br />
php &gt; $date-&gt;setDate(2016,2,30);</p>

<p>Check for errors:<br />
php &gt; var_export($date-&gt;getLastErrors());<br />
array (<br />
&nbsp; 'warning_count' =&gt; 0,<br />
&nbsp; 'warnings' =&gt;&nbsp;<br />
&nbsp; array (<br />
&nbsp; ),<br />
&nbsp; 'error_count' =&gt; 0,<br />
&nbsp; 'errors' =&gt;&nbsp;<br />
&nbsp; array (<br />
&nbsp; ),<br />
)</p>

<p>The date is set to March 1st:<br />
php &gt; echo $date-&gt;format('Y-m-d');<br />
2016-03-01</p>

<p>If the invalid date is part of the instantiation a warning is returned in getLastErrors()</p>

<p>php &gt; $date = new DateTime('2016-02-30', new DateTimeZone('UTC'));<br />
php &gt; var_export($date-&gt;getLastErrors());<br />
array (<br />
&nbsp; 'warning_count' =&gt; 1,<br />
&nbsp; 'warnings' =&gt;&nbsp;<br />
&nbsp; array (<br />
&nbsp; &nbsp; 11 =&gt; 'The parsed date was invalid',<br />
&nbsp; ),<br />
&nbsp; 'error_count' =&gt; 0,<br />
&nbsp; 'errors' =&gt;&nbsp;<br />
&nbsp; array (<br />
&nbsp; ),<br />
)<br />
php &gt; echo $date-&gt;format('Y-m-d');<br />
2016-03-01<br />
&nbsp;</p>
