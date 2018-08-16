---
title: linux 下安装 nginx
categories:
  - 服务器
date: 2018-02-24 14:49:28
tags:
  - Nginx
---

---summary--- linux 下安装nginx，安装方式分为使用yum安装和源码包安装两种方式。对比两种安装方式，我选择了源码包安装的方式进行安装。简单记录下两种安装的区别于源码安装的方式。 ---summary---

* * *

[nginx 安装包下载地址](http://nginx.org/download/)：http://nginx.org/download/

[nginx 1.5.9 源码下载地址](http://nginx.org/download/nginx-1.5.9.tar.gz)：http://nginx.org/download/nginx-1.5.9.tar.gz

* * *

yum安装和源码包安装的区别
--------------

*   yum安装是在线安装，好处是：安装简单，不易出错；
    
*   源码包安装是将 nginx 的源码下载下来，在自己的系统里编译声称可执行文件，然后执行，好处是：因为是在自己的系统上编译的，更符合自己系统的性能，也就是说在自己的心痛上执行nginx服务性能效率更好
    

**安装路径不同**

*   他们之间最大的区别是：安装路劲不同，yum在线安装会将安装文件放在系统的不同位置，结果就导致无法维护nginx的安装文件。
*   源码安装则可以自己随意指定安装目录。方便维护。

**启用方式不同**

*   yum 安装 nginx，我们可以通过 系统服务命令 service 来启动或停止

    # service nginx start #启动 nginx 服务
    
    # service nginx stop #停止 nginx 服务
    
    # service nginx restart #重启 nginx 服务
    
    

*   源码安装nginx启动的时候不能使用service来启动，需要执行nginx安装目录下的sbin目录下的nginx可执行程序才行，

    # cd nginx/sbin/
    # ./nginx  启动
    # ./nginx -s quit 停止
    # ./nginx -s reload 刷新配置
    

源码包 安装 nginx
------------

1.  下载安装包

    # wget http://nginx.org/download/nginx-1.5.9.tar.gz
    

1.  解压安装包

    # tar -zxvf nginx-1.5.9.tar.gz
    

1.  可能会缺少依赖库，所以先安装依赖库

    yum -y install pcre-devel
    
    yum -y install openssl openssl-devel
    
    

1.  安装

    # ./configure --prefix=/usr/GMX/nginx --with-http_stub_status_module --with-http_realip_module  //编译
    # make && make install //安装
    

编译参数说明：nginx大部分常用模块，编译时./configure --help以--without开头的都默认安装。

    --prefix=PATH ： 指定nginx的安装目录。默认 /usr/local/nginx
    --conf-path=PATH ： 设置nginx.conf配置文件的路径。nginx允许使用不同的配置文件启动，通过命令行中的-c选项。默认为prefix/conf/nginx.conf
    --user=name： 设置nginx工作进程的用户。安装完成后，可以随时在nginx.conf配置文件更改user指令。默认的用户名是nobody。--group=name类似
    --with-pcre ： 设置PCRE库的源码路径，如果已通过yum方式安装，使用--with-pcre自动找到库文件。使用--with-pcre=PATH时，需要从PCRE网站下载pcre库的源码（版本4.4 - 8.30）并解压，剩下的就交给Nginx的./configure和make来完成。perl正则表达式使用在location指令和 ngx_http_rewrite_module模块中。
    --with-zlib=PATH ： 指定 zlib（版本1.1.3 - 1.2.5）的源码解压目录。在默认就启用的网络传输压缩模块ngx_http_gzip_module时需要使用zlib 。
    --with-http_ssl_module ： 使用https协议模块。默认情况下，该模块没有被构建。前提是openssl与openssl-devel已安装
    --with-http_stub_status_module ： 用来监控 Nginx 的当前状态
    --with-http_realip_module ： 通过这个模块允许我们改变客户端请求头中客户端IP地址值(例如X-Real-IP 或 X-Forwarded-For)，意义在于能够使得后台服务器记录原始客户端的IP地址
    --add-module=PATH ： 添加第三方外部模块，如nginx-sticky-module-ng或缓存模块。每次添加新的模块都要重新编译（Tengine可以在新加入module时无需重新编译）
    

1.  启动 nginx

    # cd nginx/sbin/
    # ./nginx 
    

1.  停止

    # ./nginx -s quit
    

两个问题： 1 安装nginx时， 还有gcc的依赖 2修改nginx.config文件中的 use nobody 为 use root，表示使用root用户的权限。才可以访问文件，否则会出现404 的问题。

* * *

参考：https://segmentfault.com/a/1190000007116797