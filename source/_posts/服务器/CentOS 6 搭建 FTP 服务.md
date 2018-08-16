---
title: CentOS 6 搭建 FTP 服务
categories:
  - 服务器
date: 2018-02-24 18:10:59
---

文件传输协议（英文：File Transfer Protocol，缩写：FTP）是用于在网络上进行文件传输的一套标准协议，使用客户/服务器模式。它属于网络传输协议的应用层。我们要分清文件传送（file transfer）和文件访问（file access）之间的区别，前者是FTP提供的，后者是如NFS等应用系统提供的\[1\]。参考文献RFC959定义了此规范。

**概述** FTP服务一般运行在20和21两个端口。端口20用于在客户端和服务器之间传输数据流，而端口21用于传输控制流，并且是命令通向ftp服务器的进口。当数据通过数据流传输时，控制流处于空闲状态。而当控制流空闲很长时间后，客户端的防火墙会将其会话置为超时，这样当大量数据通过防火墙时，会产生一些问题。此时，虽然文件可以成功的传输，但因为控制会话，会被防火墙断开；传输会产生一些错误。 FTP虽然可以被终端用户直接使用，但是它是设计成被FTP客户端程序所控制。

**安装过程**

使用 yum 安装 vsftpd：

    sudo yum install vsftpd
    

如果需要连接其他 FTP 服务器，则可以安装 FTP 客户端。

    sudo yum install ftp
    

添加用户

    adduser userftp
    passwd userftp
    

禁止用户的 ssh 登录权限，只允许 FTP 访问:

    usermod -s /sbin/nologin userftp
    

配置 VSFTP 打开配置文件：

    sudo vi /etc/vsftpd/vsftpd.conf
    

关闭匿名访问：

    anonymous_enable=NO
    

去掉 local_enable 的注释，修改为开启：

    local_enable=YES
    

限制用户仅能访问自己的主目录：

    chroot_local_user=YES
    

设置用户的主目录：(不设置时，默认为用户的家目录/home/userftp)

    local_root=/data/test
    

重启服务：

    sudo service vsftpd restart
    

设置开机自启动：

    chkconfig vsftpd on
    

连接测试

    ftp userftp@112.126.74.124
    
    ftp> pwd
    Remote directory: /home/userftp
    
    ftp> quit
    221 Goodbye.