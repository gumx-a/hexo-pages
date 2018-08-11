---
title: npm 安装卸载及常用命令
categories:
  - 工具
date: 2018-02-24 14:41:46
tags:
  - npm
---

**安装cnpm**

npm install -g cnpm --registry=https://registry.npm.taobao.org

* * *

**卸载 node 及 npm**

1.  先通过 程序和功能 删除掉Nodejs
2.  删除以下目录（前两个是删除nodejs的，如果只删除npm，则只需要删除后两个文件夹就可以了）

    C:\Program Files (x86)\Nodejs 
    C:\Program Files\Nodejs 
    C:\Users\{User}\AppData\Roaming\npm (or %appdata%\npm) 
    C:\Users\{User}\AppData\Roaming\npm-cache (or %appdata%\npm-cache)
    

1.  先通过 程序和功能 删除掉Nodejs
2.  重启

* * *

**查看已安装的包**

    npm list -g --depth 0
    
    list： 已安装的包
    -g ：全局安装的包
    --depth 0 显示的列表深度，如果不加这个会显示详细的包路径
    

* * *

**搜索**

    cnpm search [package name]
    
    

**查看版本号列表**

    cnpm view [package name] viersions