---
title: web 跨域 HTML5 解决方案
categories:
  - 前端
date: 2018-02-24 14:42:44
tags:
  - JavaScript
---

[原文地址](http://blog.csdn.net/Ryron/article/details/72615084)

浏览器同源策略限制从一个源加载的文档或脚本如何与来自另一个源的资源进行交互。这是一个用于隔离潜在恶意文件的关键的安全机制。如果协议、端口、主机是相同的，则两个页面源相同。下表是相对于http://abc.com/同源检测

![同源检测.png](/img.api?file=[98]1510637118242.png)

[window.postMessage](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/postMessage)

### 语法

    otherWindow.postMessage(message, targetOrigin, [transfer]);
    
    // otherWindow 发送窗口，比如iframe的contentWindow
    // message 发送信息
    // targetOrigin 定哪些窗口能接收到消息事件 "*" 表示无限制
    // transfer [可选] 是一串和message 同时传递的 Transferable 对象. 这些对象的所有权将被转移给消息的接收方，而发送一方将不再保有所有权。
    

### 发送端设置Origin

在使用postMessage时需要注意的是，如果你明确的知道消息应该发送到哪个窗口，那么请始终提供一个有确切值的targetOrigin。不提供确切的目标将导致数据泄露到任何对数据感兴趣的恶意站点。

例子：3000端口页面向3001端口页面postMessage,配置targetOrigin 为http://192.168.31.235:3001。

    &lt;iframe id="iframe" src="http://192.168.31.235:3001/test"&gt;&lt;/iframe&gt;
    &lt;script type="text/javascript"&gt;
      function postMsg(){
        var msg = {psw: '123456'};
        var targetOrigin = "http://192.168.31.235:3001";
        var frame = document.getElementById('iframe');
        frame.contentWindow.postMessage(msg, targetOrigin);
      }
    &lt;/script&gt;
    

如果postMessage发送的目标不是配置的targetOrigin，浏览器就会报错,例如targetOrigin配置的是http://192.168.31.235:3001,而iframe的域是http://192.168.31.235:3002。

    Failed to execute 'postMessage' on 'DOMWindow': The target origin provided ('http://192.168.31.235:3002') does not match the recipient window's origin ('http://192.168.31.235:3001').
    

### 接收端检测Origin

为了防止恶意站点发送postMessage,接收端同样需要检测Origin。

3001端口（与3000跨域）接受来自3000端口的postMessage,判断是否是目标源，如果是继续工作，否则不做处理。

    window.addEventListener("message", onReceivedMessage, false);
    function onReceivedMessage(event){
        var origin = event.origin || event.originalEvent.origin;
        if(origin === 'http://192.168.31.235:3000'){
                // do something
            }else{
                return;
            }
    }