---
title: Ubuntu15.10上搭建Express服务器
date: 2016-07-15 14:02:43
tags:
---
由于我的虚拟机上装的是ubuntu15.10，所以是在这个系统的基础上安装的。

看第一条命令：

```
sudo apt-get update && sudo apt-get install nodejs-legacy npm
```
我把这条命令拆分一下，

```
sudo apt-get update 是更新系统。

sudo apt-get install nodejs-legacy npm 是安装nodejs-legacy 和npm。
```
紧接着执行 Express官网的安装命令

```
$ npm install express --save
```


