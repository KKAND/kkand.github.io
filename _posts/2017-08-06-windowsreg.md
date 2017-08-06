---
layout: post
title: Windows reg
description: add or change reg
date: 2017-08-06 19:57:07 +08:00
tags: 
 - windows
---
# Windows reg

## 修改注册表
 - 修改或者删除注册表最好先进行备份
 - 不要随意添加注册表，防止......
 - 保存为.reg文件运行即可导入注册表
 - 在导入的.reg文件中加-即可删除导入的注册表
```
如将
[HKEY_CLASSES_ROOT\folder\shell\cmd]
改为
[-HKEY_CLASSES_ROOT\folder\shell\cmd]
就可以除去刚刚导入的注册表文件
```

### 右键添加cmd

 - 在文件夹中打开命令行cmd
 - 最简单的方式是按shift再按右键即可看到打开命令行的选项
 - 另外一种，在注册表中注册，一下是代码，复制后保存为.reg文件运行

```
Windows Registry Editor Version 5.00  
; Created by: Shawn Brink  
; http://www.sevenforums.com  
; Tutorial: http://www.sevenforums.com/tutorials/47415-open-command-window-here-administrator.html  
[-HKEY_CLASSES_ROOT\Directory\shell\runas]  
[HKEY_CLASSES_ROOT\Directory\shell\runas]  
@="Open cmd here as Admin"  
"HasLUAShield"=""  
[HKEY_CLASSES_ROOT\Directory\shell\runas\command]  
@="cmd.exe /s /k pushd \"%V\""  
[-HKEY_CLASSES_ROOT\Directory\Background\shell\runas]  
[HKEY_CLASSES_ROOT\Directory\Background\shell\runas]  
@="Open cmd here as Admin"  
"HasLUAShield"=""  
[HKEY_CLASSES_ROOT\Directory\Background\shell\runas\command]  
@="cmd.exe /s /k pushd \"%V\""  
[-HKEY_CLASSES_ROOT\Drive\shell\runas]  
[HKEY_CLASSES_ROOT\Drive\shell\runas]  
@="Open cmd here as Admin"  
"HasLUAShield"=""  
[HKEY_CLASSES_ROOT\Drive\shell\runas\command]  
@="cmd.exe /s /k pushd \"%V\""
```

 -  效果
 <img src="{{site.url}}/assets/pictures/cmd.png" width="150px" />

[参考自-温暖的博客](http://blog.csdn.net/qq_19244423/article/details/46662293)