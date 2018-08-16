---
title: 记一些复杂的 MySQL 语句记录
tags:
  - MySQL
categories:
  - 数据库
date: 2018-02-24 13:57:38
---

*   查询所有重复的记录

    Select * From 表 Where 重复字段 In (Select 重复字段 From 表 Group By 重复字段 Having Count(*)&gt;1) 
       

*   过滤重复记录 只显示重复记录中一条 ID 最大的记录

    Select * From 表 Where ID In (Select Max(ID) From 表 Group By 重复字段)  
    

*   更新时数据使用查询语句的结果

    // order 要更新的表名
    //number 要更新的字段
    //获取年龄大于10的所有数据中 number的最大值
    //将获取到的值存储到 k2 虚表中，
    //修改id=10的这条数据
    
    UPDATE order,
    (SELECT MAX(number) AS u FROM order  WHERE age&gt;10 )k2
    SET number=k2.u+1 WHERE id=10
    

*   分组查询,并且只返回每个分组的最大值

    select a.* from table(要查的表) a,(select id,max(age(最大值的依据)) age from table   group by city(分组条件)) b where  a.id= b.id and a.age= b.age order by a.city