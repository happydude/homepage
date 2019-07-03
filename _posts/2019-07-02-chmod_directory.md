---
author: Jason Davis
layout: post
title: chmod 700 on directories, 600 on files
---

Want to give execute on all directories but not all files?

```bash
chmod -Rv u=rwX,g=,o- /media/32GBflash
```

-R = recursive
-v = verbose
