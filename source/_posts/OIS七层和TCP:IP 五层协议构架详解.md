---
title: OIS七层和TCP/IP 五层协议构架详解
categories:
  - 后端
date: 2018-02-24 14:22:30
tags:
  - 网络
---

开放式系统互联通信参考模型（英语：Open System Interconnection Reference Model，缩写为 OSI），简称为OSI模型（OSI model），一种概念模型，由过期标准组织（ISO）提出，一个试图使各种计算机在世界范围内互联为网络的标准框架。 --维基百科 

| OSI中的层 | 功能                  | TCP/IP协议族                                 |
| ------ | ------------------- | ----------------------------------------- |
| 应用层    | 文件传输/电子邮件/文件服务/虚拟终端 | TFTP,HTTP,SNMP TCP/IP,TFP,SMTP,DNS,Telnet |
| 表示层    | 数据格式化,代码转换,数据加密     | 没有协议                                      |
| 会话层    | 解除或建立与别的节点的联系       | 没有协议                                      |
| 传输层    | 提供端对端的接口            | TCP UDP                                   |
| 网络层    | 为数据包选择路由            | IP, ICMP,RIP,OSPF,BGP,IGMP                |
| 数据链路层  | 传输有地址的帧以及错误检测功能     | SLIP,CSLIP,PPP,ARP,RARP,MTU               |
| 物理层    | 以二进制数据的形式在物理媒体上传输数据 | ISO2110,IEEE802,IEE802.2                  |