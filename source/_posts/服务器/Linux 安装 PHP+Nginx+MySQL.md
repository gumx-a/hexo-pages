---
title: Linux 安装 PHP+Nginx+MySQL
categories:
  - 服务器
date: 2018-02-23 15:24:06
---

### Step 1 – Setup Yum Repository

我们用yum安装软件时,经常发现我们的yum源里面没有该软件，需要自己去wget，然后configure,make,make install，太折腾了。

其实，CentOS还有一个源叫做 EPEL (Extra Packages for Enterprise)，里面有1万多个软件，比163的源还强，强烈建议安装。

1、安装前，我们先看一下我们现有的源：

![enter image description here](http://gumx.top/wp-content/uploads/2018/02/OB9_Q5FZ9CPI@KHX201-1-1.png)

如图所示，当前源有8127个软件。

2、安装EPEL YUM源

    yum install epel-release
    rpm -Uvh http://rpms.famillecollet.com/enterprise/remi-release-7.rpm
    rpm -Uvh http://repo.mysql.com/mysql-community-release-el7-5.noarch.rpm
    

### Step 2 – Install PHP 7

### Step 3 – Install NGINX

### Step 4 – Install MySQL 5.6

### Step 5 – Setup PHP-FPM

### Step 6 – Restart Services

### Step 7. Verify Setup