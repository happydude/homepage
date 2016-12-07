---
layout: post
title: Fun with javascript Date
---

<p>JavaScript seems to accept invalid dates similarly to php:</p>

<p>&nbsp;</p>

<p>var date = new Date("February 31, 2016");</p>

<p>console.log(date);</p>

<p>&nbsp;</p>

<p>Wed Mar 02 2016 00:00:00 GMT-0700 (MST)</p>

<p>&nbsp;</p>

<p>It does appear that js draws the line at day 32:</p>

<p>var date = new Date("February 32, 2016");<br />
console.log(date);<br />
Invalid Date</p>
