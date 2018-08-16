---
title: Java 基本数据类型
categories:
  - 后端
date: 2018-02-24 14:17:20
tags:
  - Java
---

基本类型可以分为三类，字符类型 char，布尔类型 boolean 以及数值类型 byte、short、int、long、float、double。

参考来源： http://wiki.jikexueyuan.com/project/java-special-topic/type-operation.html

基本类型可以分为三类，字符类型 char，布尔类型 boolean 以及数值类型 byte、short、int、long、float、double。数值类型又可以分为整数类型 byte、short、int、long 和浮点数类型 float、double。JAVA中的数值类型不粗在无符号的，他们的取值范围时固定的，不会随着机器硬件环境或者操作系统的改变而改变。

![数据类型.png](http://upload-images.jianshu.io/upload_images/4580053-91e6365db9dd8ea2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  

取值范围和数据长度：

基本类型：byte 二进制位数：8 包装类：java.lang.Byte 最小值：Byte.MIN\_VALUE=-128 最大值：Byte.MAX\_VALUE=127

基本类型：short 二进制位数：16 包装类：java.lang.Short 最小值：Short.MIN\_VALUE=-32768 最大值：Short.MAX\_VALUE=32767

基本类型：int 二进制位数：32 包装类：java.lang.Integer 最小值：Integer.MIN\_VALUE=-2147483648 最大值：Integer.MAX\_VALUE=2147483647

基本类型：long 二进制位数：64 包装类：java.lang.Long 最小值：Long.MIN\_VALUE=-9223372036854775808 最大值：Long.MAX\_VALUE=9223372036854775807

基本类型：float 二进制位数：32 包装类：java.lang.Float 最小值：Float.MIN\_VALUE=1.4E-45 最大值：Float.MAX\_VALUE=3.4028235E38

基本类型：double 二进制位数：64 包装类：java.lang.Double 最小值：Double.MIN\_VALUE=4.9E-324 最大值：Double.MAX\_VALUE=1.7976931348623157E308

基本类型：char 二进制位数：16 包装类：java.lang.Character 最小值：Character.MIN\_VALUE=0 最大值：Character.MAX\_VALUE=65535 ``\`