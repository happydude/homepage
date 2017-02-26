---
author: Jason Davis
layout: post
title: Fun with javascript Date
---

<p>JavaScript appears to accept invalid dates in a similarl way to php:</p>

```javascript
var date = new Date("February 31, 2016");

console.log(date);

Wed Mar 02 2016 00:00:00 GMT-0700 (MST)
```
 
Javascript (at least in chrome) draws the line at day 32:
```javascript
var date = new Date("February 32, 2016");
console.log(date);
Invalid Date
```
