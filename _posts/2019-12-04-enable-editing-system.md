---
author: Jason Davis
layout: post
title: Make /system writable on user debug android builds
---

Make /system writable on user debug android builds

```bash
adb root
adb disable-verity
adb reboot

#run adb root again
adb root
adb remount
adb shell
mount -o rw,remount /system
```

... do stuff ...

Turn dm-verity back on

```bash
adb root
adb enable-verity
```
