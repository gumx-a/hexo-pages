---
title: MyEclipse 设置
tags:
  - MyEclipse
categories:
  - 工具
date: 2018-02-24 14:21:28
---

记录下MyEclipse常用的各种设置。

### 去掉js验证

解决办法：

Windows->Preferences->Myeclipse->Validation (js,jsp content, jsp syntax去掉) 项目属性->Builders->javascript去掉

* * *

### MyEclipse 总是不停的在 Update index

原因： Update index...是Maven在下载更新

解决办法：

Window --> Preferences --> Myeclipse Enterprise Workbench --> Maven4Myeclipse --> Maven --> 去除Download repository index updates on startup前的勾选即可。

* * *

### 字体设置

Window---->Preferences--->General--->Appearance--->Colors and Fonts--->Basic--->Text Font

* * *

### 编码格式

Window---->Preferences--->General--->Workspace

* * *

### 换行

Window---->Preferences--->Java--->Code Style--->Formatter

* * *

### 修改html、jsp等文件的默认打开方式

Window---->Preferences--->General--->Editors--->File Associations