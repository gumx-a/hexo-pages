---
title: 修改SSH端口
categories:
  - 服务器
date: 2018-02-24 14:04:59
tags:
  - SSH
---

修改配置文件/etc/ssh/sshd_config，可以改ssh登录端口和禁止root登录。改端口可以防止被端口扫描。

编辑配置文件：

    vim /etc/ssh/sshd_config
    

找到#Port 22，去掉注释，修改成一个五位的端口：Port 12333 找到#PermitRootLogin yes，去掉注释，修改为： PermitRootLogin no

重启sshd服务：

    service sshd restart