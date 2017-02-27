---
title: 解决Xcode模拟器显示UDID bug
date: 2016-07-01 16:34:24
tags:
---

* 1 、彻底关闭Xcode跟模拟器
* 2 、终端内输入 -> sudo killall -9 com.apple.CoreSimulator.CoreSimulatorService
* 3 、终端内继续输入 -> rm -rf ~/Library/Developer/CoreSimulator/Devices
* 4 、重启Xcode。


