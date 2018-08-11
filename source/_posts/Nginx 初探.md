---
title: Nginx 初探
categories:
  - 服务器
date: 2018-02-24 14:50:02
tags:
  - Nginx
---

* * *

**什么是 Nginx**

Nginx 是由俄罗斯人编写的十分轻量级的==HTTP服务器==，Nginx，他的发音为 "engine X"，是一个高性能的==HTTP反向代理服务器==，同时也是一个==IMAP/POP3/SMTP代理服务器==。

英文主页： http：//nginx.net

到2013年，国内已经有很多网站采用Nginx作为Web服务器，如国内知名的新浪、162、腾讯、淘宝的过。据netcraft统计，Nginx排名第三，约占15%的份额。

Nginx以事件驱动的方式编写，所以有非常好的性能，同时也是一个非常搞笑的反向代理、负载平衡。其拥有匹配Lighttpd的性能，同时还没有Lighttpd的内存泄露问题。

* * *

**Nginx 特点** Nginx 做为 HTTP 服务器，有以下几项基本特性：

*   处理静态文件，索引文件及自动索引；打开文件描述缓冲。
*   无缓存的反向代理加速，简单的负载均衡和容错。
*   FastCGI，简单的负载均衡和容错。
*   模块化的结构。包括gzipping、byte ranges、chunked responses 以及SSI-filter等filter。如果由FastCGI或其他代理服务器处理单页中存在的多个SSI，则这项处理可以并行运行，而不需要相互等待。
*   支持SSL和TLSSNI

Nginx转为性能优化而开发，性能是其重要的考量，事实上非常注重效率。它支持内核Poll模型，能经受高负载的考验，有报告表名能支持高达50000个并发连接数。

Nginx具有很高的稳定性。

Nginx支持热部署。

* * *

[参考](http://wiki.jikexueyuan.com/project/nginx/basic-concept.html)： http://wiki.jikexueyuan.com/project/nginx/basic-concept.html