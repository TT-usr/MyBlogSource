---
title: DDL语句（部分整理）
date: 2017-03-07 09:22:11
tags:   
    - MySQL
---
创建表
    
    CREATE TABLE t_person(name text, age INTEGER );
    
`注意`可以执行没有效果但是要保证执行正确
如果不存在才创建

    CREATE table if not EXISTS t_person(name text,age interger , score real)；

删除表
    
    DROP table t_person；
如果存在再删除
    
    DROP table if EXISTS t_person；

修改表名

    ALTER table t_stu rename to t_student;

添加列
    
    ALTER TABLE t_student add column address text；

测试，数据库表，字段是没有数据类型的
**但是**要求必须写，SQL规范

    CREATE TABLE t_person(name , age  );

约束

* 不能为空
    `not null`
* 不能重复
    ``
* 默认值

        CREATE table t_abc(id integer PRIMARY key AUTO_INCREMENT ,name text not null , age INTEGER DEFAULT 99 ,score real UNIQUE);
          释义：
        -- PRIMARY key 主键
        -- AUTO_INCREMENT 自动增长（可直接设置初始值例如： AUTO_INCREMENT=100）
        -- not null 不为空
        -- UNIQUE 唯一


    

