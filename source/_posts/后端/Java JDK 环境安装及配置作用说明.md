---
title: Java JDK 环境安装及配置作用说明
categories:
  -  后端
date: 2018-02-24 14:16:37
tags:
  - Java
---


作用说明
----

*   Path: 配置Path的目的是因为 在JDK 下的bin文件夹中有很多我们在开发中使用的工具,如java.exe, javac.exe,jar.ex等, 那么我们在使用时,想要在电脑的任意位置下使用这些java开发工具,那么我们就需要把这些工具所在的路径配置到系统的环境变量中,当我们使用时,系统可以帮助我们找到这些命令.
    
*   JAVA\_HOME: 有时候我们可能需要经常更换jdk的目录,但是经常修改path的值,可能会不小心修改其他的路径,所以作为一个解决办法,就是创建一个中间变量JAVA\_HOME用来存储jdk的值,然后再将JAVA_HOME作为一个映射配置给Path
    
*   CLASSPATH: 类路径classPath环境变量通常用来记录当前路径和 java库所在的路径在类库中包含java系统所提供的各种软件包,其中包含各个类的接口等.
    

* * *

Windows版:
---------

### 1\. 安装jdk

安装JDK 选择安装目录 安装过程中会出现两次 安装提示 。第一次是安装 jdk ，第二次是安装 jre 。建议两个都安装在同一个java文件夹中的不同文件夹中。（不能都安装在java文件夹的根目录下，jdk和jre安装在同一文件夹会出错） 如下图所示

\[![JDK安装与环境变量配置](http://upload-images.jianshu.io/upload_images/4580053-2fcbfa94c3bf7f4d.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 2\. 配置环境变量

安装完JDK后配置环境变量  计算机→属性→高级系统设置→高级→环境变量

\[![JDK安装与环境变量配置](http://upload-images.jianshu.io/upload_images/4580053-5ccbbbabeeac2267.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### 2.1 添加 JAVA_HOME

系统变量→新建 JAVA_HOME 变量 变量值填写jdk的安装目录（本人是 E:\\Java\\jdk1.7.0)

#### 2.2 修改 PATH

系统变量→寻找 Path 变量→编辑 在变量值最后输入 %JAVA\_HOME%\\bin;%JAVA\_HOME%\\jre\\bin; （注意原来Path的变量值末尾有没有;号，如果没有，先输入；号再输入上面的代码）

[![JDK安装与环境变量配置](http://upload-images.jianshu.io/upload_images/4580053-ae99bd2f027fa5d1.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)](http://jingyan.baidu.com/album/6dad5075d1dc40a123e36ea3.html?picindex=5)

#### 2.3 添加 CLASSPATH

系统变量→新建 CLASSPATH 变量 变量值填写   .;%JAVA\_HOME%\\lib;%JAVA\_HOME%\\lib\\tools.jar（注意最前面有一点） 系统变量配置完毕

\[![JDK安装与环境变量配置](http://upload-images.jianshu.io/upload_images/4580053-c0b2a0f8620bc984.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 3 检验安装结果

检验是否配置成功 运行cmd 输入 java -version （java 和 -version 之间有空格） 若如图所示 显示版本信息 则说明安装和配置成功。

\[![JDK安装与环境变量配置](http://upload-images.jianshu.io/upload_images/4580053-a135c3e3e00c47ee.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* * *

## Mac版: (待整理)
---------------

Linux版:
-------

linux下三种配置环境变量的方法:

### 1\. 修改/etc/profile文件

如果你的计算机仅仅作为开发使用时推荐使用这种方法，因为所有用户的shell都有权使用这些环境变量，可能会给系统带来安全性问题。 ·用文本编辑器打开/etc/profile ·在profile文件末尾加入：

    JAVA_HOME=/usr/java/jdk1.7.0_80
    JRE_HOME=/usr/java/jdk1.7.0_80/jre
    PATH=$PATH:$JAVA_HOME/bin:$JRE_HOME/bin
    CLASSPATH=:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar:$JRE_HOME/lib
    export JAVA_HOME JRE_HOME PATH CLASSPATH
    
    

·注解 a. 你要将 /usr/share/jdk1.6.0\_14改为你的jdk安装目录 b. linux下用冒号“:”来分隔路径 c. $PATH / $CLASSPATH / $JAVA\_HOME 是用来引用原来的环境变量的值 在设置环境变量时特别要注意不能把原来的值给覆盖掉了，这是一种 常见的错误。 d. CLASSPATH中当前目录“.”不能丢,把当前目录丢掉也是常见的错误。 e. export是把这三个变量导出为全局变量。 f. 大小写必须严格区分。

### 2.修改.bash_profile文件

这种方法更为安全，它可以把使用这些环境变量的权限控制到用户级别，如果你需要给某个用户权限使用这些环境变量，你只需要修改其个人用户主目录下的.bash\_profile文件就可以了。 ·用文本编辑器打开用户目录下的.bash\_profile文件 ·在.bash_profile文件末尾加入：

    export JAVA_HOME=/usr/share/jdk1.6.0_14
    export PATH=$JAVA_HOME/bin:$PATH
    export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
    

### 3.直接在shell下设置变量

不赞成使用这种方法，因为换个shell，你的设置就无效了，因此这种方法仅仅是临时使用，以后要使用的时候又要重新设置，比较麻烦。 只需在shell终端执行下列命令：

    export JAVA_HOME=/usr/share/jdk1.6.0_14
    export PATH=$JAVA_HOME/bin:$PATH
    export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
    

*   source 文件路径(使修改生效)
*   java -version 查看版本