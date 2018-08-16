---
title: SSH 登录命令
categories:
  - 服务器
date: 2018-02-24 14:06:17
tags:
  - SSH
---

ssh命令用于远程登录上[Linux](http://lib.csdn.net/base/linux)主机。 常用格式：ssh \[-l login_name\] \[-p port\] \[user@\]hostname

举例 不指定用户：

    ssh 192.168.0.11
    

指定用户：

    ssh -l root 192.168.0.11
    
    ssh root@192.168.0.11
    

如果修改过ssh登录端口的可以：

    ssh -p 12333 192.168.0.11
    
    ssh -l root -p 12333 216.230.230.114
    
    ssh -p 12333 root@216.230.230.114