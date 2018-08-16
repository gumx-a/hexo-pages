---
title: Nginx 匹配规则
categories:
  - 服务器
date: 2018-08-16 14:44:18
tags:
  - Nginx
---

## location 匹配规则

	location [=|~|~*|^~] /uri/ { … }


模式	|含义
----|:---
location = /uri		|	= 表示精确匹配，只有完全匹配上才能生效
location ^~ /uri	|	^~ 开头对URL路径进行前缀匹配，并且在正则之前。
location ~ pattern	|	开头表示区分大小写的正则匹配
location ~* pattern	|	开头表示不区分大小写的正则匹配
location /uri		|	不带任何修饰符，也表示前缀匹配，但是在正则匹配之后
location /			|	通用匹配，任何未匹配到其它location的请求都会匹配到，相当于switch中的default

## 多个 location 配置的情况下匹配顺序为:


* 首先精确匹配 =
* 其次前缀匹配 ^~
* 其次是按文件中顺序的正则匹配
* 然后匹配不带任何修饰的前缀匹配。
* 最后是交给 / 通用匹配
* 当有匹配成功时候，停止匹配，按当前匹配规则处理请求
