---
title: mysql条件语句(简单)
date: 2017-03-08 15:33:31
tags:
---
    
* where 字段 ！= 值
* where 字段 is not 值
* where 字段 < 值
* where 字段 > 值
* where 字段 = 值 and 字段 = 值
* where 字段 = 值 or 字段 = 值

```sql
UPDATE t_stu set name = 'nj' WHERE num = 4;

DELETE FROM t_stu WHERE score < 60 and age < 18
```

