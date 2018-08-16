---
title: Linux 中文乱码
categories:
  - 服务器
date: 2018-02-24 14:20:30
---

由于某些原因系统安装时未安装中文支持，导致后续应用出现中文方块乱码现象，解决方法很简单，当然不是重装，只需以下三步即可搞定。

查看当前系统字符编码配置

    # locale
    

1、安装中文包：

    #yum -y groupinstall chinese-support    安装所有与中文支持相关的包
     ```
    
    2、修改字符编码配置文件
    

vi /etc/sysconfig/i18n
======================

修改后内容如下： LANG="zh\_CN.UTF-8" SUPPORTED="zh\_CN:zh:en\_US.UTF-8:en\_US:en:zh_CN.GB18030" SYSFONT="latarcyrheb-sun16"

    3、最后重启服务器：
    
    

reboot
======

```