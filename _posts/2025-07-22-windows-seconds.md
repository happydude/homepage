---
author: Jason Davis
layout: post
title: Add seconds to windows task bar clock
---

```powershell
Set-ItemProperty -Path HKCU:\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced -Name ShowSecondsInSystemClock -Value 1 -Force
```
