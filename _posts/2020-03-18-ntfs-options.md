---
author: Jason Davis
layout: post
title: my ntfs-3g options
---
Source [ntfs-3g options](https://www.tuxera.com/community/ntfs-3g-manual/#6)

#Options
* ro read-only
* windows_names - limits valid file names
* locale=en_US.utf8
* uid=1000 - first user
* gid=1000 - first group
* dmask=077 - subtract from 777 for directories (drwx------)
* fmask=177 - substract from 777 for files (-rw-------)

```fstab
UUID="123XYZ" /media/windows ntfs ro,windows_names,locale=en_US.utf8,uid=1000,gid=1000,dmask=077,fmask=177 1 1
```

