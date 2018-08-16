---
title: Mac 编译安装 Nginx
tags:
  - nginx
categories:
  - 服务器
date: 2018-05-20 08:38:07
---

1.下载 Nginx 源码包
--------------

> 下载页: http://nginx.org/en/download.html 当前稳定版本: http://nginx.org/download/nginx-1.8.0.tar.gz

2.下载编译选项中的依赖包
-------------

### zlib

> 当前稳定版本: zlib-1.2.8.tar.gz 注: Nginx 参考文档中提到需要 1.1.3 – 1.2.7 版本的 zlib

pcre

> 当前稳定版本:pcre-8.32.tar.gz 注: Nginx 参考文档中提到需要 4.4 – 8.32 版本的 pcre

3.解压依赖源码包
---------

4.编译安装 Nginx
------------

这里会将各依赖的源码编译进 Nginx, 所以 –with-zlib 和 –with-pcre 后为对应的依赖源码目录路径。此外, 编译选项中还开启了 HTTPS 的协议支持 --with-http\_ssl\_module, 若不需要 HTTPS, 可取消该选项。

    cd nginx-1.8.0    
    ./configure --prefix=/usr/local/nginx --with-zlib=../zlib-1.2.8 --with-pcre=../pcre-8.32
    sudo make && make install
    

5.编译安装完成, 测试启动、重启、停止:
---------------------

    cd /usr/local/nginx
    #启动
    sudo sbin/nginx     #浏览器访问 127.0.0.1 测试是否成功启动
    #重启
    sudo sbin/nginx -s reload
    #停止
    sudo sbin/nginx -s stop