---
author: Jason Davis
layout: post
title: Fun with javascript Date
---

<p>JavaScript seems to accept invalid dates similarly to php:</p>

```javascript
var date = new Date("February 31, 2016");

console.log(date);

 

Wed Mar 02 2016 00:00:00 GMT-0700 (MST)

 

It does appear that js draws the line at day 32:

var date = new Date("February 32, 2016");
console.log(date);
Invalid Date
```
