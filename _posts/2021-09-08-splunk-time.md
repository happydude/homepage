---
author: Jason Davis
layout: post
title: Apache Combined Log Format microtime and Splunk 
---

{% raw %}
Repurpose the unused ident field in apache combined log with ```%{%s}t.%{usec_frac}t ```, looks like 1631118098.166000 in the log file

Then in splunk search ```something | eval _time = strftime(ident,"%Y-%m-%dT%H:%M:%S.%Q%z")```
{% endraw %}
