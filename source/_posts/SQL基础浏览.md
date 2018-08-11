---
title: SQL基础浏览
categories:
  - 数据库
date: 2018-03-13 07:44:05
tags:
  - MySQL
---

[SQL基础](http://www.runoob.com/sql/sql-function.html)
====================================================

SQL 简介
------

SQL是用于访问和处理数据库的标准的计算机语言

### SQL是什么?

*   SQL，指结构化查询语言，全称是 Structured Query Language。
*   SQL 让您可以访问和处理数据库。
*   SQL 是一种 ANSI（American National Standards Institute 美国国家标准化组织）标准的计算机语言。

### SQL能做什么?

*   SQL 面向数据库执行查询
*   SQL 可从数据库取回数据
*   SQL 可在数据库中插入新的记录
*   SQL 可更新数据库中的数据
*   SQL 可从数据库删除记录
*   SQL 可创建新数据库
*   SQL 可在数据库中创建新表
*   SQL 可在数据库中创建存储过程
*   SQL 可在数据库中创建视图
*   SQL 可以设置表、存储过程和视图的权限

### 常用的MySQL管理命令:

*   USE Databasename 用于在MySQL工作区内选择具体某个数据库。
*   SHOW DATABASES 列出 MySQL DBMS 所能访问的数据库。
*   SHOW TABLES 一旦数据库被 use 命令选中，显示数据库中的表。
*   SHOW COLUMNS FROM tablename 显示表的属性、属性类型、键信息、是否允许 NULL 值，默认值，以及其他一些信息。
*   SHOW INDEX FROM tablename 显示表中所有索引的细节信息，包括PRIMARY KEY。
*   SHOW TABLE STATUS LIKE tablename\\G 报告MySQL DBMS的性能及统计的细节信息。

### SQL SELECT

SELECT语句用于从数据库中选取数据,**结果被存储在一个结果表中,称为结果集**

### SQL SELECT IDSTINCT

返回唯一不同的值(去除重复的值).

### SQL WHERE

用于过滤记录.

#### WHERE字句中的运算符

运算符

描述

=

等于

<>

不等于。注释：在 SQL 的一些版本中，该操作符可被写成 !=

>

大于

<

小于

>=

大于等于

<=

小于等于

BETWEEN

在某个范围内

LIKE

搜索某种模式

IN

指定针对某个列的多个可能值

#### 特殊条件

1.  空值判断: is null
2.  between and (在 ... 之间的值)
3.  in
4.  like

### SQL AND & OR

### ORDER BY 用于对结果集进行排序

默认按照升序对记录进行排序.

*   DESC 升序
*   ASC 降序

### SQL INSERT INTO

用于向表中插入新记录。

INSERT INTO 语句可以有两种编写形式。 第一种形式无需指定要插入数据的列名，只需提供被插入的值即可：

    INSERT INTO table_name
    VALUES (value1,value2,value3,...);
    

第二种形式需要指定列名及被插入的值：

    INSERT INTO table_name (column1,column2,column3,...)
    VALUES (value1,value2,value3,...);
    

### SQL UPDATE

用于更新表中已经存在的记录

### SQL DELETE

用于删除表中已经存在的记录

SQL 高级函数
--------

### SQL SELECT TOP

MySQL中 TOP 无效.

MySQL语法:

    SELECT column_name(s) FROM table_name LIMIT number;
    

Oracle 语法

    SELECT column_name(s)
    FROM table_name
    WHERE ROWNUM <= number;
    

SQL SELECT TOP PERCENT 示例: 使用百分比作为参数

    SELECT TOP 50 PERCENT * FROM Websites;
    

### SQL LIKE

搜索列中的制定模式

SQL LIKE 语法

    SELECT column_name(s)
    FROM table_name
    WHERE column_name LIKE pattern;
    

### SQL 通配符

通配符用于替换字符串中任何其他字符

MySQL中使用REGEXP或NOT REGEXP运算符(或者LIKE和NOT LIKE)来操作正则表达式

SQL中可以使用一下通配符

通配符

描述

%

替代0个或者多个字符

-

替代一个字符

\[charlist\]

字符列中的任何单一字符

\[^charlist\]或者\[!charlis\]

不在字符列中的任何单一字符

### SQL IN

### SQL BETWEEN

SQL BETWEEN 语法(两头都包括):

BETWEEN 操作符选取介于两个值之间的数据范围内的值。这些值可以是数值、文本或者日期。

    SELECT column_name(s)
    FROM table_name
    WHERE column_name BETWEEN value1 AND value2;
    

NOT BETWEEN , NOT IN: 不在范围内

### SQL 别名

通过使用SQL,可以为表名或者列名指定列名.基本上，创建别名是为了让列名称的可读性更强。

将多个列和在一起:

    SELECT name, CONCAT(url, ', ', alexa, ', ', country) AS site_info
    FROM Websites;
    

在下面的情况下，使用别名很有用：

*   在查询中涉及超过一个表
*   在查询中使用了函数
*   列名称很长或者可读性差
*   需要把两个列或者多个列结合在一起

### SQL 连接(JOIN)

SQL join 用于把来自两个或者多个表的行结合起来.

在我们继续讲解实例之前，我们先列出您可以使用的不同的 SQL JOIN 类型：

*   INNER JOIN：如果表中有至少一个匹配，则返回行
*   LEFT JOIN：即使右表中没有匹配，也从左表返回所有的行
*   RIGHT JOIN：即使左表中没有匹配，也从右表返回所有的行
*   FULL JOIN：只要其中一个表中存在匹配，则返回行

* * *

#### 1.SQL INNER JOIN 语法

    SELECT column_name(s)
    FROM table1
    INNER JOIN table2
    ON table1.column_name=table2.column_name;
    

或：

    SELECT column_name(s)
    FROM table1
    JOIN table2
    ON table1.column_name=table2.column_name;
    

**注释：INNER JOIN 与 JOIN 是相同的。**

#### 2\. SQL LEFT JOIN 语法

    SELECT column_name(s)
    FROM table1
    LEFT JOIN table2
    ON table1.column_name=table2.column_name;
    

或：

    SELECT column_name(s)
    FROM table1
    LEFT OUTER JOIN table2
    ON table1.column_name=table2.column_name;
    

**注释：在某些数据库中，LEFT JOIN 称为 LEFT OUTER JOIN。**

#### 3\. SQL RIGHT JOIN 语法

    SELECT column_name(s)
    FROM table1
    RIGHT JOIN table2
    ON table1.column_name=table2.column_name;
    
    

或：

    SELECT column_name(s)
    FROM table1
    RIGHT OUTER JOIN table2
    ON table1.column_name=table2.column_name;
    

**注释：在某些数据库中，RIGHT JOIN 称为 RIGHT OUTER JOIN。**

#### 4\. SQL FULL OUTER JOIN 语法

    SELECT column_name(s)
    FROM table1
    FULL OUTER JOIN table2
    ON table1.column_name=table2.column_name;
    

### SQL UNION 操作符

SQL UNION 操作符合并两个或者多个SELECT语句的结果, 注意: UNION内部的每个SELECT语句必须拥有相同数量的列.列也必须拥有相似的数据类型.同事每个SELECT语句中的列的顺序也必须相同.

SQL UNION 语法

    SELECT column_name(s) FROM table1
    UNION
    SELECT column_name(s) FROM table2;
    

**注释：默认地，UNION 操作符选取不同的值。如果允许重复的值，请使用 UNION ALL。**

SQL UNION ALL 语法

    SELECT column_name(s) FROM table1
    UNION ALL
    SELECT column_name(s) FROM table2;
    

**注释：UNION 结果集中的列名总是等于 UNION 中第一个 SELECT 语句中的列名。**

### SQL SELECT INTO 语句

通过SQL,您可以从一个表复制信息到另一个表.

MySQL 数据库不支持 SELECT ... INTO 语句，但支持 INSERT INTO ... SELECT 。 当然你可以使用以下语句来拷贝表结构及数据：

    CREATE TABLE 新表 SELECT * FROM 旧表
    

### SQL INSERT INTO SELECT 语句

INSERT INTO SELECT 语句从一个表复制数据，然后把数据插入到一个已存在的表中。目标表中任何已存在的行都不会受影响。

SQL INSERT INTO SELECT 语法 我们可以从一个表中复制所有的列插入到另一个已存在的表中：

    INSERT INTO table2
    SELECT * FROM table1;
    

或者我们可以只复制希望的列插入到另一个已存在的表中：

    INSERT INTO table2
    (column_name(s))
    SELECT column_name(s)
    FROM table1;
    

### SQL CREATE DATABASE 语句

用于创建数据库

    CREATE DATABASE dbname;
    

### SQL CREATE TABLE 语句

CREATE TABLE 语句用于创建数据库中的表。

实例

    CREATE TABLE Persons
    (
    PersonID int,
    LastName varchar(255),
    FirstName varchar(255),
    Address varchar(255),
    City varchar(255)
    );
    

### SQL 约束

SQL约束用于规定表中的数据规则.

在SQL中有如下约束:

*   NOT NULL -只是某列不能存储null值
*   UNIQUE - 保证某列的每行必须有唯一的值
*   PRIMARY KEY - NOT NULL 和 UNIQUE 的结合,确保某列的值有唯一标识,有助于更快速的找到表中的一个特定的记录.
*   FOREIGN KEY -保证一个表中的数据匹配到另一个表中的值得参照完整性.
*   CHECK -保证列中的值负荷指定的条件.
*   DEFAULT - 规定没有给列赋值时的默认值.

#### ALERT TABLE 时的 SQL约束(修改约束)

当表已被创建时，如需在 "P_Id" 列创建 UNIQUE 约束，请使用下面的 SQL：

    ALTER TABLE Persons
    ADD UNIQUE (P_Id)
    

#### 撤销约束

如需撤销 UNIQUE 约束，请使用下面的 SQL： MySQL：

    ALTER TABLE Persons
    DROP INDEX uc_PersonID
    

SQL Server / Oracle / MS Access：

    ALTER TABLE Persons
    DROP CONSTRAINT uc_PersonID
    

### SQL CREATE INDEX

用于创建索引.在不读取整表的情况下,索引使数据库应用程序可以更快的查找数据.

**注释：**更新一个包含索引的表需要比更新一个没有索引的表花费更多的时间，这是由于索引本身也需要更新。因此，理想的做法是仅仅在常常被搜索的列（以及表）上面创建索引。

CREATE INDEX 实例

下面的 SQL 语句在 "Persons" 表的 "LastName" 列上创建一个名为 "PIndex" 的索引：

    CREATE INDEX PIndex
    ON Persons (LastName)
    

如果您希望索引不止一个列，您可以在括号中列出这些列的名称，用逗号隔开：

    CREATE INDEX PIndex
    ON Persons (LastName, FirstName)
    

SQL CREATE UNIQUE INDEX 语法:在表上创建一个唯一的索引。不允许使用重复的值：唯一的索引意味着两个行不能拥有相同的索引值.

### SQL DROP

使用DROP语句,删除索引,表和数据库.

*   删除数据库

    DROP DATABASE database_name
    

*   删除表

    DROP TABLE table_name
    

*   删除索引

    ALTER TABLE table_name DROP INDEX index_name
    

*   TRUNCATE TABLE 语句(清空表内数据)

    TRUNCATE TABLE table_name
    

### SQL ALTER TABEL语句

用于在已有的表中添加,删除或者修改列.

*   添加列

    ALTER TABLE table_name
    ADD column_name datatype
    

*   删除列

    ALTER TABLE table_name
    DROP COLUMN column_name
    

*   修改列的数据类型

    ALTER TABLE table_name
    MODIFY COLUMN column_name datatype
    

### SQL AUTO INCREMENT 字段

自增的字段.

*   设置表内自增字段起始值

    ALTER TABLE Persons AUTO_INCREMENT=100
    

### SQL 视图.

可以理解为对查询的封装;

*   添加视图

    CREATE VIEW view_name AS
    SELECT column_name(s)
    FROM table_name
    WHERE condition
    

*   删除视图

    DROP VIEW view_name
    

*   修改视图

    CREATE OR REPLACE VIEW view_name AS
    SELECT column_name(s)
    FROM table_name
    WHERE condition
    

使用视图

    select * from view_name; 
    

### SQL 日期

MySQL 使用下列数据类型在数据库中存储日期或日期/时间值：

*   DATE - 格式：YYYY-MM-DD
*   DATETIME - 格式：YYYY-MM-DD HH:MM:SS
*   TIMESTAMP - 格式：YYYY-MM-DD HH:MM:SS
*   YEAR - 格式：YYYY 或 YY

日期函数:

函数

描述

NOW()

返回当前的日期和时间

CURDATE()

返回当前的日期

CURTIME()

返回当前的时间

DATE()

提取日期或日期/时间表达式的日期部分

EXTRACT()

返回日期/时间的单独部分

DATE_ADD()

向日期添加指定的时间间隔

DATE_SUB()

从日期减去指定的时间间隔

DATEDIFF()

返回两个日期之间的天数

DATE_FORMAT()

用不同的格式显示日期/时间

### SQL NULL

NULL代表遗漏的未知数据. 使用 IS NULL 和 NOT IS NULL 作为筛选条件.

*   IS NULL

    SELECT LastName,FirstName,Address FROM Persons
    WHERE Address IS NULL
    

*   IS NOT NULL

    SELECT LastName,FirstName,Address FROM Persons
    WHERE Address IS NOT NULL
    

### SQL NULL 函数

MySQL中使用IFNULL()函数.当所选字段值为NULL时 给予默认值.

    SELECT (1+IFNULL(fee,0))as a from ss_order
    

SQL 函数
------

SQL Aggregate 函数

SQL Aggregate 函数计算从列中取得的值，返回一个单一的值。 有用的 Aggregate 函数：

*   AVG() - 返回平均值
*   COUNT() - 返回行数
*   FIRST() - 返回第一个记录的值
*   LAST() - 返回最后一个记录的值
*   MAX() - 返回最大值
*   MIN() - 返回最小值
*   SUM() - 返回总和
*   SQL Scalar 函数

SQL Scalar 函数基于输入值，返回一个单一的值。 有用的 Scalar 函数：

*   UCASE() - 将某个字段转换为大写
*   LCASE() - 将某个字段转换为小写
*   MID() - 从某个文本字段提取字符
*   LEN() - 返回某个文本字段的长度
*   ROUND() - 对某个数值字段进行指定小数位数的四舍五入
*   NOW() - 返回当前的系统日期和时间
*   FORMAT() - 格式化某个字段的显示方式