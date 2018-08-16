---
title: 数据库管理系统（来自wki）
categories:
  - 数据库
date: 2018-02-24 14:07:29
tags:
	数据库管理系统
---

1\. 数据库管理系统
-----------

[数据库管理系统](https://zh.wikipedia.org/wiki/%E6%95%B0%E6%8D%AE%E5%BA%93%E7%AE%A1%E7%90%86%E7%B3%BB%E7%BB%9F)（英语：Database Management System，简称DBMS）是为管理[数据库](https://zh.wikipedia.org/wiki/%E8%B3%87%E6%96%99%E5%BA%AB)而设计的电脑[软件](https://zh.wikipedia.org/wiki/%E8%BB%9F%E9%AB%94)系统，一般具有存储、截取、安全保障、备份等基础功能。数据库管理系统可以依据它所支持的[数据库模型](https://zh.wikipedia.org/w/index.php?title=%E8%B3%87%E6%96%99%E5%BA%AB%E6%A8%A1%E5%9E%8B&action=edit&redlink=1)来作分类，例如[关系式](https://zh.wikipedia.org/wiki/%E9%97%9C%E8%81%AF%E6%A8%A1%E5%9E%8B)、[XML](https://zh.wikipedia.org/w/index.php?title=XML%E8%B3%87%E6%96%99%E5%BA%AB&action=edit&redlink=1)；或依据所支持的电脑类型来作分类，例如服务器群集、移动电话；或依据所用查询语言来作分类，例如[SQL](https://zh.wikipedia.org/wiki/SQL)、[XQuery](https://zh.wikipedia.org/w/index.php?title=XQuery&action=edit&redlink=1)；或依据性能冲量重点来作分类，例如最大规模、最高运行速度；亦或其他的分类方式。不论使用哪种分类方式，一些DBMS能够跨类别，例如，同时支持多种查询语言。

2 类型
----

### 2.1 关系数据库

*   [MySQL](https://zh.wikipedia.org/wiki/MySQL)

### 2.2 非关系数据库

*   [MongoDB](https://zh.wikipedia.org/wiki/MongoDB)

#### 2.2.1 键值数据库

3 数据库模型
-------

*   [对象模型](https://zh.wikipedia.org/w/index.php?title=%E7%89%A9%E4%BB%B6%E6%A8%A1%E5%9E%8B&action=edit&redlink=1)
*   层次模型（轻量级数据访问协议）
*   网状模型（大型数据储存）
*   关系模型
*   面向对象模型
*   半结构化模型
*   [平面模型](https://zh.wikipedia.org/w/index.php?title=%E5%B9%B3%E9%9D%A2%E6%A8%A1%E5%9E%8B&action=edit&redlink=1)（表格模型，一般在形式上是一个二维[数组](https://zh.wikipedia.org/wiki/%E6%95%B0%E7%BB%84)。如表格模型数据[Excel](https://zh.wikipedia.org/wiki/Excel))

3.1 构架
------

数据库的架构可以大致区分为三个概括层次：内层、概念层和外层。 \* 内层：最接近实际存储体，亦即有关数据的实际存储方式。 \* 外层：最接近用户，即有关个别用户观看数据的方式。 \* 概念层：介于两者之间的间接层。

### 3.2 数据库索引

**数据库索引**，是[数据库管理系统](https://zh.wikipedia.org/wiki/%E6%95%B0%E6%8D%AE%E5%BA%93%E7%AE%A1%E7%90%86%E7%B3%BB%E7%BB%9F)中一个排序的[数据结构](https://zh.wikipedia.org/wiki/%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84)，以协助快速查询、更新[数据库表](https://zh.wikipedia.org/wiki/%E6%95%B0%E6%8D%AE%E5%BA%93%E8%A1%A8)中数据。

### 3.3 数据库操作,事务

事务（transaction）是用户定义的一个数据库操作序列，这些操作要么全做，要么全不做，是一个不可分区的工作单位。 事务的[ACID](https://zh.wikipedia.org/wiki/ACID)特性： *基元性（atomicity） * 一致性（consistency） * 隔离性（isolation） * 持续性（durability）

事务的并发性是指多个事务的并行操作轮流交叉运行，事务的并发可能会访问和存储不正确的数据，破坏交易的隔离性和数据库的一致性。