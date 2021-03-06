---
title: Linux系统在SSH客户端关闭后继续运行程序
categories:
  - 服务器
date: 2018-06-23 07:25:58
tags:
  - SSH
---

由于各种原因，需要通过ssh登录linux或者unix主机，很多时候我们需要通过ssh的终端启动一 些服务或者运行一些程序，但是默认情况下，当我们关闭ssh终端连接，随之启动的程序也会关闭。原因是：SSH会话关闭时，ssh所关联的pty关闭，系统会给这个pty所关联的session中的所有进程发送SIGHUP信号，SIGHUP的默认信号处理程序是终止进程，除非进程自己处理了 SIGHUP。

解决方法如下：

使用现成的命令nohup，可以让指定的程序在pty关闭之后继续运行。

    nohup ./target &
    

现在就可以正常关闭ssh了，你会发现你的服务依然存在运行，运行的输出结果默认输出到nohup.out文件中，可以重新定义文件进行输出：

    nohup ./target > a.out &
    

这样程序的输出结果就输出到了a.out文件中了。