---
title: Mybatis 插入数据后获取主键
categories:
  - 后端
date: 2018-02-23 14:56:41
tags:
  - Java
---

方法一:

    <insert id="insertAuthor" useGeneratedKeys="true" keyProperty="id"> 
        insert into Author (username,password,email,bio) values (#{username},#{password},#{email},#{bio}) 
    </insert>