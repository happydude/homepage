---
author: Jason Davis
layout: post
title: chmod 700 on directories, 600 on files
---

Want to give full rights including execute on all directories but not all files? Use capital X instead of x.

```bash
chmod -Rv u=rwX,g=,o= /mnt/path
```
u= user
-R = recursive
-v = verbose
