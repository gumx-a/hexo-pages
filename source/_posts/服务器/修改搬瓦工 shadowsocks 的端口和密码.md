---
title: 修改搬瓦工 shadowsocks 的端口和密码
categories:
  - 服务器
date: 2018-02-24 17:31:42
---

大部分购买搬瓦工的童鞋，主要的作用基本上都是启用shadowsocks，如果你是从控制面板那里直接点击安装的，一般来说都不能随意更改密码，但是你如果又有这种需求咋办呢？其实很好办，只需要修改这两个文件：

    修改端口 vi /root/.kiwivm-shadowsocks-port 
    修改密码 vi /root/.kiwivm-shadowsocks-password