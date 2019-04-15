---
title: Linux 安装 Node 并将目录软连接到全局环境下（简单使用）
categories:
  - 服务器
tags:  
- Node
date: 2018-12-10 15:14:56
---

### 1. 下载 nodejs 的 Linux 版本并解压到任意目录。

下载地址： http://nodejs.cn/download/


	~ wget https://npm.taobao.org/mirrors/node/v10.14.1/node-v10.14.1.tar.gz
	~ tar -zxvf node-v10.14.1



### 2. 将目录软链接到全局环境下


	ln -s /deploy/node-v8.11.3-linux-x64/bin/node /usr/local/bin/node
	ln -s /deploy/node-v8.11.3-linux-x64/bin/npm /usr/local/bin/npm
