---
author: Jason Davis
layout: post
title: Curl with a host header
---

Use the -H header option to add a Host: header with the desired virtual host name.

```
curl -H 'Host: crazymonkey.test' http://127.0.0.1
```
