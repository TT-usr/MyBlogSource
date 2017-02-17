---
title: React-Native踩坑之旅系列一：Invariant Violation:Application 项目名 has not been registered
date: 2017-02-15 10:42:02
tags:
        - react-native
---

**错误提示**

Invariant Violation:Applicaction 项目名 has not been registered.This is either due to a require() error during initialization or failure to call AppRegistry.registerCommponent.

![](http://upload-images.jianshu.io/upload_images/1435825-afa737fbfecf445c.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**解决方案一：**

这个错误的根本原因是根目录./index.ios.js中

```js
AppRegistry.registerComponent('项目名',() => ...);
```
与./ios/项目名/appDelegate.m中的

```oc
RCTRootView*rootView = [[RCTRootViewalloc]initWithBundleURL:jsCodeLocation

moduleName:@"项目名" launchOptions:launchOptions];
```
或是./android/app/src/main/java/com/项目名/MainActivity.java中的

```java
mReactRootView.startReactApplication(mReactInstanceManager, "项目名", null);
```
没有保持一致，解决方法很简单。编辑成相同的参数即可。

如果发现不是此问题，那么就看看解决方案二吧。

**解决方案二、**

即便你确保一致了但还是出现相同的错误提示，这又是怎么搞得呢？这个时候你可以检查一下你的命令行。有可能你同时在运行一个以上的程序，像我。如果你的react-native在运行程序A而你打开了程序B，也会出现相同的问题。解决方法很简单，关掉命令行运行程序。ctrl+c,运行你想运行的程序。
记住，是系统的终端，不是你使用的ITerm2终端。

    

