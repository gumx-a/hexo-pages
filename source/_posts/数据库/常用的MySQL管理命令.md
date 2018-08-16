---
title: 常用的MySQL管理命令
categories:
  - 数据库
date: 2018-03-13 07:55:17
tags:
  - MySQL
---

    MySQL 目前是最流行的开源关系型 SQL 数据库管理系统，是一种用于最适于开发 Web 软件应用的 RDBMS。

### 常用的MySQL管理命令:

*   USE Databasename 用于在MySQL工作区内选择具体某个数据库。
*   SHOW DATABASES 列出 MySQL DBMS 所能访问的数据库。
*   SHOW TABLES 一旦数据库被 use 命令选中，显示数据库中的表。
*   SHOW COLUMNS FROM tablename 显示表的属性、属性类型、键信息、是否允许 NULL 值，默认值，以及其他一些信息。
*   SHOW INDEX FROM tablename 显示表中所有索引的细节信息，包括PRIMARY KEY。
*   SHOW TABLE STATUS LIKE tablename\\G 报告MySQL DBMS的性能及统计的细节信息。