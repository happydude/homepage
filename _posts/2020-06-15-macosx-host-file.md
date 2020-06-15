---
author: Jason Davis
layout: post
title: Mac OS X host file and cache clear
---
The file:
```
/private/etc/hosts
```

Clear Cache:
```bash
sudo killall -HUP mDNSResponder
```
