---
title: windows 下 Nginx 的启动、停止、重启、重新载入命令
categories:
  - 服务器
date: 2018-02-24 14:46:37
tags:
  - Nginx
---

Nginx (engine x) 是一款轻量级的Web 服务器 、反向代理服务器及电子邮件（IMAP/POP3）代理服务器。发布版本分为 Linux 和 windows 版本。windows下为了安装 Nginx，需先下载它。然后解压之，然后运行即可。Nginx 是运行在一个控制台程序，而非 windows 服务方式的。服务器方式目前还是开发尝试中。

\### windows 下 Nginx 的启动、停止、重启、重新载入命令 ###
-----------------------------------------

常用命令行如下：

    nginx -s stop       快速关闭Nginx，可能不保存相关信息，并迅速终止web服务。
    nginx -s quit       平稳关闭Nginx，保存相关信息，有安排的结束web服务。
    nginx -s reload     因改变了Nginx相关配置，需要重新加载配置而重载。
    nginx -s reopen     重新打开日志文件。
    nginx -c filename   为 Nginx 指定一个配置文件，来代替缺省的。
    nginx -t            不运行，而仅仅测试配置文件。nginx 将检查配置文件的语法的正确性，并尝试打开配置文件中所引用到的文件。
    nginx -v            显示 nginx 的版本。
    nginx -V            显示 nginx 的版本，编译器版本和配置参数。
    
    

使用案例：

**1\. 启动**

    C:\server\nginx-1.0.2>start nginx
    或
    C:\server\nginx-1.0.2>nginx.exe
    
    

**2\. 停止**

    C:\server\nginx-1.0.2>nginx.exe -s stop
    或
    C:\server\nginx-1.0.2>nginx.exe -s quit
    
    

注：stop是快速停止nginx，可能并不保存相关信息；quit是完整有序的停止nginx，并保存相关信息。

**3\. 重新载入Nginx**

    C:\server\nginx-1.0.2>nginx.exe -s reload
    
    

当配置信息修改，需要重新载入这些配置时使用此命令。

**4\. 查看Nginx版本**

    C:\server\nginx-1.0.2>nginx -v
    
    

**5\. 检查配置文件语法的正确性。**

    C:\server\nginx-1.0.2>nginx -t
    
    

不运行，而仅仅测试配置文件。nginx 将检查配置文件的语法的正确性，并尝试打开配置文件中所引用到的文件。