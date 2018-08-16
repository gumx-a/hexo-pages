---
title: linux JDK1.7 安装与配置
categories:
  - 后端
date: 2018-02-24 14:34:43
tags:
  - JDK
---

linux JDK1.7 安装与配置

### 1\. 新建文件夹，下载jdk，并解压

[jdk 下载地址](http://www.oracle.com/technetwork/java/javase/archive-139210.html)：http://www.oracle.com/technetwork/java/javase/archive-139210.html

    cd /
    mkdir java
    cd java
    wget http://download.oracle.com/otn/java/jdk/7u80-b15/jdk-7u80-linux-x64.tar.gz?AuthParam=1513056626_7ecb8f96cf15eaee78d9d1bb26add842
    tar -zxvf 文件名
    

### 2.配置环境变量

用文本编辑器打开/etc/profile

    vim /etc/profile
    

在profile文件末尾加入

    JAVA_HOME=/java/jdk1.7.0_80
    JRE_HOME=/java/jdk1.7.0_80/jre
    PATH=$PATH:$JAVA_HOME/bin:$JRE_HOME/bin
    CLASSPATH=:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar:$JRE_HOME/lib
    export JAVA_HOME JRE_HOME PATH CLASSPATH
    

### 3\. 使修改生效,查看安装结果

    source 文件路径
    java -version