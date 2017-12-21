---
author: Jason Davis
layout: post
title: Windows 10 Startup folder
---

The old school startup folder still exists on Windows 10 but it is a bit buried now.
But, no worries, the startup folder is just a short Run box command away.

short
```winbatch
shell:startup
```
medium
```winbatch
"%APPDATA%\Microsoft\Windows\Start Menu\Programs\Startup"
```
long
```winbatch
C:\Users\%USERNAME%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup
```
