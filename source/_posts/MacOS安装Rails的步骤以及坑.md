---
title: MacOS安装Rails的步骤以及坑
date: 2016-07-16 13:44:03
tags:
---
一、MacOS自带ruby为2.0.0版本,如果你想装最新版的Rails需要更新到ruby2.2.4版本.
更新系统自带ruby步骤:
* 安装 RVM
RVM:Ruby Version Manager,Ruby版本管理器，包括Ruby的版本管理和Gem库管理(gemset)

``` ruby
$ curl -L get.rvm.io | bash -s stable
```
等待一段时间后就可以成功安装好 RVM。
如果不关闭命令行就想使RVM生效,需要执行以下两行命令

```ruby
$ source ~/.bashrc  
$ source ~/.bash_profile
```
当然关闭命令行再次打开也会使得RVM生效的
测试RVM是否工作正常

```ruby
$ rvm -v 
```
<!--more-->
![测试RVM工作是否正常.png](http://upload-images.jianshu.io/upload_images/900667-4b4168906fa09ff3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 用RVM升级Ruby

```ruby
#查看当前ruby版本  
$ ruby -v  
ruby 2.0.0  
#列出已知的ruby版本  
$ rvm list known  
#安装ruby 2.3  (首先安装Rails最新版的前提就是ruby的version不能低于2.2.4)
$ rvm install 2.3
```
安装完成之后ruby -v查看是否安装成功。
![确认安装完成后的ruby版本信息](http://upload-images.jianshu.io/upload_images/900667-d50f43b00f033dd3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

二、安装HomeBrew
* 安装brew

```ruby
# For Mac
# 先安装 [Xcode](http://developer.apple.com/xcode/) 开发工具，它将帮你安装好 Unix 环境需要的开发包
# 然后安装 [Homebrew](http://brew.sh)
$ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
* OS X 安装 Rails 必要的一些三方库
```ruby
$ brew install libxml2 libxslt libiconv
```

三、安装 Bundler(没有搜索过这个有什么用,以后再深入.)

```ruby
$ gem install bundler
```

四、安装 Rails 环境(这里有一个MacOS的坑,不注意就掉进去)
上面 3 个步骤过后，Ruby 环境就安装好了，接下来安装 Rails

```ruby
$ gem install rails
```

然后测试安装是否正确

```ruby
$ rails -v
Rails 4.2.5
```
注意!!!
是否可能会遇到类似于博主的状况

![遇到的问题](http://upload-images.jianshu.io/upload_images/900667-e30f830576b58406.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
这个原因在于没有安装Xcode Command Line Tools,但是实际上撸主已经安装过Xcode了,并且已经设定好了Command Line Tools 的版本

![CommandLine Tools已经安装了](http://upload-images.jianshu.io/upload_images/900667-380823083c5bd8b3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

但是依旧不好用

最后是怎么解决的呢?请看下面

```ruby
# 请在命令行工具中执行
$ xcode-select --install
```
![安装Command Line Tools](http://upload-images.jianshu.io/upload_images/900667-a8d3b765646a8f72.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

会弹出提示框,让你安装Command Line Tools,
安装以后就可以继续愉快的安装Rails.

最后祝大家Rails玩的愉快😬

参考文献:

>* [如何快速正确的安装 Ruby, Rails 运行环境](https://ruby-china.org/wiki/install_ruby_guide)
* [error-to-install-nokogiri-on-osx-10-9-maverick](http://stackoverflow.com/questions/19643153/error-to-install-nokogiri-on-osx-10-9-maverick)

