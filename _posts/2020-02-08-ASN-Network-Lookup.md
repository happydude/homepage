---
author: Jason Davis
layout: post
title: Find all subnets of an ASN
---

Find all subnets for ASN209 (CenturyLink)

```bash
whois -h whois.radb.net -- '-i origin AS209'
```
filter to subnets
```bash
whois -h whois.radb.net -- '-i origin AS209' |grep ^route
```
