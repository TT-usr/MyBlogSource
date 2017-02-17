---
title: JSPatch踩过坑的部分语句（更新中。。）
date: 2016-10-27 14:42:09
tags:
---
# JSPatch使用笔记

> JSPatch就没必要去细说了，用过的人都知道它的好，但是让没有接触过的人很容易迷惑怎么去写热修复的脚本。下面就是博主使用此三方框架的一些踩坑成果、

**JSPatch中的（）是用于函数调用**

| 情况 | OC | JSPatch |
| --- | --- | --- |
| 基础变量必须初始化 | CGFloat lastPointX ;| var lastPointX = 0.0; |
| 获取当前页面的私有属性 | _minPointValue | self.valueForKey("_minPointValue") |
| 获取CGPoint结构体的值<br>宽度与高度同理 | self.maxPointLabel.frame.origin.y  | self.maxPointLabel().frame().y |
| 获取结构体的值 | NSRange | range.location 即可 |
| 定义Point | CGPointMake(lastPointX,y) | {x: lastPointX, y: y} |
| 定义Size | CGSizeMake(5,5) | {width: 5, height:5} |
| Surper的使用 | super | self.super() |
| 数组根据索引取值 | self.points[i] | self.points().objectAtIndex(i) |

