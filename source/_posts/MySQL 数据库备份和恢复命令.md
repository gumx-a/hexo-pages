---
title: MySQL 数据库备份和恢复命令
date: 2018-02-23 16:17:00
categories: ['数据库']
tags: ['MySQL']
---

以下命令在windows与linux下通用


### 备份数据库

    mysqldump -uroot -p test table1 > d:\ct.txt
    

### 恢复数据库

    mysql  -uroot  -p database_name < d:\aa.txt