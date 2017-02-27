---
title: Something about cocoapods & 组件化
date: 2017-02-27 10:16:38
tags:
        - cocoapods
---

**前言：**
周末参加了一次组件化的学习，iOS上的组件化的基础就是cocoapods 下面就复习一下cocoapods，内容包含：

* 安装
* **使用（重点）**
    * 1.使用cocoapods 官方库
        * 安装第三方库
        * 第三方的子库
    * **2.使用私有库（重点）**
        * 如何创建本地pod库
        * 如何创建本地以及远程私有仓库
        * 如何添加远程私有库到本地远成仓库
        * 如何两种（私有以及官方库）仓库共同使用
* 其他pod相关的命令操作

### 一.Git
> cocoapods 少不了Git，所以先把cocoapods能用到的相关Git知识补充一下

**a.基础**

```
// 添加文件到暂存区
git add .

// 提交到仓库
git commit ''

// 推送到远程仓库
git push origin 分支

// 如果没有关联远程仓库
git remote add origin 远程仓库地址

```

**b.标签(cocoapods基础，决定你所用的库的版本)**

```
//添加本地标签
git tag -a ‘版本号’ -m ‘描述'
或
git tag 版本号

// 删除本地标签
git tag -d 标签

// 讲本地tag推送到远程
git push - -tags

// 删除远程标签
git push origin :标签


```

### 二、cocoapods

**A.Podfile相关**

    1.生成方式
        * 通过pod init方式生成（推荐，会生成模板信息）
        * 通过手动创建文件生成
    2.podfile相关参数
        * source 仓库源（可指定多个，组件化所需基础）
        * platform 指定操作系统和版本
        * ...（其余都知道了就不再赘述）

**B.Pod一些常识**
    
    1. 1.0版本后`pod install`不会默认调用更新本地仓库导致天朝程序员痛苦不堪的等待，
    而1.0版本之前，如果调用`pod install`不添加`no-update-repo`会更新本地仓库
    
    2. `pod install` 会默认先判断本地是否有`lock`文件，如果有`lock`文件，`pod` 会默认加载`lock`内部记录的库版本信息， 

    3. `pod`的缓存路径为 `~/cache/cocoapod/`

    4. 框架以及索引信息路径`~/.cocoapods/repos/master `

**C.本地私有库** 

    1.创建命令： `pod spec creat 项目名`
    2.使用本地库的podfile需要描述其路径：
    pod 'xxx', :path=> '路径/xxx.spec'
    
**D.远程私有库**

    1.创建私有spec仓库
    2.添加到pod中： `pod repo add 仓库名 c`
    3.创建私有库所需项目工程文件并上传私有仓库
    4.创建spec 填写完并在本地测试
    5.验证spec文件  `pod lib init`
    6.提交私有spec到私有spec仓库 `pod repo push SpecName xxx.podspec`
    7.使用时别忘记添加私有spec源到你的podfile文件

### 三、组件化

**A.介绍**

a.基本概念

    将一个单一工程的项目, 分解成为各个独立的组件; 然后按照某种方式, 任意组织成一个拥有完整业务逻辑的工程

b.产生原因

    注意: 如果是单一工程, 业务线比较少, 人数比较少, 一般的开发模式没有任何问题,
    但是一旦项目发展慢慢庞大, 业务主线增多,开发人员增多, 就会暴露出一系列问题
    * 耦合比较严重
    * 编译速度慢
    * 测试不独立
    * 无法使用自己擅长的设计模式
    * ...

c.优势
    
    组件的独立
        * 独立编写
        * 独立编译
        * 独立运行
        * 独立测试
    
    资源重用
        * 功能代码的重复使用

    高效的迭代
        * 增删模块


    ** 可配合二进制化, 最大化的提高项目编译速度

d.出现的问题
    
    * 需要把哪些内容划分成为一个组件?
    * 每个组件以一个什么样的形式存在?
    * 以怎样的形式集成各个组件?
    * 组件之间如何通讯?
    
**静待更新啦。。**

