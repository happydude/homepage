---
author: Jason Davis
layout: post
title: Windows Scripts Cheatsheet
---

In days of yore I was a windows admin, this is old my old script cheat sheet.

Delete a reg key from HKEY_CLASSES_ROOT, this was a hack to make an msi uninstall with a missing transform file.
```winbatch
reg delete HKCR\Installer\Products\4EA42A62D9304AC4784BF238120651FF /v Transforms /f
```
Silent delete a directory
```winbatch
rmdir /S /Q "C:\NALCache\Tree\Xyz\install"
```
Grant all users full rights to a folder
```winbatch
cacls "C:\path" /e /p users:F /T
```
Rights to file (lacks /T)
```winbatch
cacls "C:\path" /e /p users:F
```
Run a command in a new cmd.exe
```winbatch
cmd.exe /c something.exe
```
Grant registry key rights with a sct file
```winbatch
regini "C:\mysctfile.sct"
```
sct file (I forget what the numbers mean)
```
\Registry\Machine\Software\Sony Media Software\Sound Forge\8.0\License [1 5 7]
```
Kill tasks based on exe name
```winbatch
taskkill /f /im "calc.exe"
```
List of running processes 
```winbatch
qprocess
```
Set a reg key value
/f removes prompt
/d data to be inputed
/t Type of Reg
/v Value of subkey you want to change
```winbatch
HKLM\Software\MyApp /v Channel /t REG_DWORD /d 5 /f
```
Stop or start service from the command line.
```winbatch
net Stop service name
net Start service name
```
Disable Service
```winbatch
sc config [Service Name] start=disabled
```
Uninstall msi via GUID
GUIDs are found in "HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall"
```winbatch
msiexec.exe /x {guid} /options
```

Start an exe and exit batch without waiting
```winbatch
start C:\appname
EXIT
```
