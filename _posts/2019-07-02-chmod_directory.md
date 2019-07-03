---
author: Jason Davis
layout: post
title: chmod 700 on directories, 600 on files
---

Want to give full rights including execute on all directories but not all files? Use capital X instead of x.

```bash
chmod -Rv u=rwX,g=,o- /media/32GBflash
```
u= user
-R = recursive
-v = verbose
