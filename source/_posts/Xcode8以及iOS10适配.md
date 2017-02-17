---
title: Xcode8以及iOS10适配
date: 2016-09-20 13:33:04
tags:
---

# 一、证书管理
用Xcode8打开工程后，比较明显的就是Automatically manage signing了，这个是苹果的新特性，可以帮助我们自动管理证书。(其实并不建议你勾选,我用的时候就把线上的生产证书搞掉了,如果是集体开发,那么你就很有可能背锅了)


![1.png](http://oe7165rae.bkt.clouddn.com/image/yaotiancheng.cn/1.png)

关于证书经常会遇到的问题:

1.>Xcode未设置开发者账号情况下的截图

![2.png](http://oe7165rae.bkt.clouddn.com/image/yaotiancheng.cn/2.png)


