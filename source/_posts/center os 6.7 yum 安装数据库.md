---
title: center os 6.7 yum 安装数据库
tags:
  - MySQL
categories:
  - 数据库
date: 2018-02-23 15:06:02
---

删除旧的mysql
---------

### 第1步、查看CentOS下是否已安装mysql

    # yum list installed | grep mysql
    

### 第2步、删除已安装mysql

    # yum -y remove mysql 
    

看到complete就说明成功了 

#### 2 删除残留文件

彻底删除mysql的方法: 1. 执行第二步,删除服务 2. 删除关联文件

    查看残留的目录： whereis mysql
    然后删除mysql目录： rm –rf /usr/lib64/mysql
    删除相关文件： rm –rf /usr/my.cnf rm -rf /root/.mysql_sercret 
    最关键的： rm -rf /var/lib/mysql
    

### 第3步、查看yum库中的mysql（非必须）

    # yum list | grep mysql
    

### 第4步、从yum库中的安装mysql

    # yum -y install mysql mysql-server mysql-devel 
    

### 第5步、验证是否安装成功

    # rpm -qi mysql-server 
    

### 第6步、启动MySql服务，设置开机自启

    1, service mysqld start 启动服务
    1. chkconfig --list 查看当前开机自启配置
    2. chkconfig mysqld on 启用开机自启
    

### 第7步、进入MySql

    # mysql -u root 
    

### 第8步、修改user 用户密码

    # mysql -u root mysql 
    mysql> UPDATE user SET Password=PASSWORD(’newpassword’) where USER=’root’; 
    mysql>  FLUSH PRIVILEGES; 
    mysql>  quit 
    # /etc/init.d/mysqld restart 
    # mysql -uroot -p 
    Enter password: > 输入新设的密码newpassword&gt; 
    mysql>