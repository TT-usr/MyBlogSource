---
title: DML语句（增删改）
date: 2017-03-08 15:24:32
tags:   
    - MySQL
---
**插入语句**
`如果是一个文本类型，需要添加‘’`

    INSERT into T_stu(name, age, score,num) VALUES ('zhangsan',12,23,1);
    
**更新语句**
    
    UPDATE t_stu set NAME = 'zhangsan', age = 20
**删除语句**
**drop** table
**delete** 操作记录

    DELETE FROM t_stu

