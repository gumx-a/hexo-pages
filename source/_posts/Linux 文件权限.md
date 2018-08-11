---
title: Linux 文件权限
categories:
  - 服务器
date: 2018-02-24 14:39:46
---

Linux系统中的每个文件和目录都有访问许可权限，用它来确定谁可以通过何种方式对文件和目录进行访问和操作。

1.  chmod 555 scriptname 允许任何人都具有可读权和执行权限。
    
2.  chmod +rx scriptname 允许任何人都具有可读权和执行权限
    
3.  chmod u+rx scriptname 只给脚本的所有者可读和执行权限
    
4.  chmod 777 *.sh 给.sh文件可执行权限。