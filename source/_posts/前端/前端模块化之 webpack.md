---
title: 前端模块化之 webpack
categories:
  - 前端
date: 2018-02-24 14:40:53
tags:
  - webpack
---

[Webpack 中文指南](http://zhaoda.net/webpack-handbook/index.html)

[Webpack 中文文档](https://doc.webpack-china.org/concepts/)

[Webpack GitHub 官网地址](http://webpack.github.io/docs/)

刚开始做web前端的项目时,页面中用到了无数的js,无数的引用,然后一个页面上万行的代码,作为从iOS转来的我,从一开始都无法忍受这么庞大的页面. 一直想看看web 前端的模块化思想,奈何刚开始技术太差,项目时间也比较紧,没有时间去深究,于是就继续扩展那一万行的代码, 哈哈.

后来开始逐渐在新项目中使用requirejs + vue 已实现初步的模块化,但是require打包这一块用着实在是不爽,之后再慕课网上看到一个webpack的教程,之前一直以为这是一个很复杂的东西.花了两个小时看完教程之后,发现原来并不复杂,完全可以用在新项目中. 今天又闲来无事自己看着上面的教程敲了一遍,挺好用.教程写的很好,向作者致敬!

总结下试过的流程(详细的命令就不记录了,只记一下遇到的问题):

1.  安装: 安装的时候, 不要全局安装,刚开始学习阶段,搞局部安装就可以,这样可以试试各个版本,貌似有了全局的安装,就不能再搞局部的安装了.
2.  package.js 中添加webpack的依赖后,安装依赖,才可以创建webpack.config.js文件,这个文件是webpack的配置文件.才可以配置loaders