---
title: 搭建hexo博客到自己的VPS
tags:
        - Linux
---

> 说明一下配置：
> 电脑操作系统：MacOS
> VPS操作系统 ：搬瓦工Centos6

<h4>Hexo安装在本机</h4>

    1. npm install hexo-cli -g #全局安装hexo脚手架工具
    2. hexo init blog #初始化项目,命名为blog
    3. cd blog
    4. npm install #安装依赖库
    5. hexo server #启动nodejs服务, 访问localhost:4000可预览


<h4>准备工作</h4>

假设本地已经安装好hexo环境，需要防盗服务器上供公网访问。首先准备好以下条件：

    1.购买服务器。我买的是位于搬瓦工服务器,国内免备案。同时搬瓦工服务器提供一键安装shaowdsocks，从此便可以愉快的翻墙了。（也可以使用脚本，稍后会提供另外一篇blog写明配置）
    
    2.购买域名。可以从万网购买,之后在控制台进行域名解析即可。（域名解析请Google吧）

<h4>服务器配置</h4>
<h5>登录服务器</h5>

购买服务器以后，可通过`ssh`登录服务器操作

    ssh root@ipaddress -p port #ipaddress和port可从供应商处获取，默认为22号端口

<h5>安装相关软件</h5>
**git**

    yum install git

**配置git**
    
    git config --global user.email "emial地址"
    git config --global user.name "用户名"

**配置git仓库(通过git hook完成自动部署)**

    cd /opt #进入opt目录
    mkdir hexo.git #创建hexo.git文件夹
    cd hexo.git
    git init --bare #初始化仓库
    cd hooks #进入git钩子脚本目录
    touch post-receive #创建post-receive
    chmod +x post-receive #增加可执行权限

*post-receive文件是当接收到git提交的数据后会执行的钩子脚本，接下来需要编辑该文件。*

    vi post-receive #编辑post-receive文件

**内容如下, 具体信息请看注释**

    #! /bin/bash -l
    echo "接收到提交"
    GIT_REPO=/opt/hexo.git # Git 项目路径（与你上面初始化的仓库地址路径相同）
    TMP_GIT_CLONE=/tmp/64mb # 临时路径
    PUBLIC_WWW=/var/www/html/blog/public   # Web 目录
    rm -rf ${TMP_GIT_CLONE} # 删除临时路径下的文件
    git clone $GIT_REPO $TMP_GIT_CLONE  # 将提交上来的文件 clone 到临时路径
    rm -rf ${PUBLIC_WWW}/*  # 删除 Web 目录下的文件
    cp -rf ${TMP_GIT_CLONE}/* ${PUBLIC_WWW} # 临时路径下的文件复制到 Web 目录下

*编辑完成按esc,输入:wq保存*

*上面脚本中将仓库转存到了/var/www/html/blog/public中。*


**Ngnix**

**安装nginx**

1.安装编译工具及库文件
    
    yum install gcc
    yum install -y pcre pcre-devel
    yum install -y zlib zlib-devel
    yum install -y openssl openssl-devel

2.下载解压nginx。下载地址可从`http://nginx.org/download`右击复制链接获取

    cd /
    mkdir nginx-src && cd nginx-src
    wget http://nginx.org/download/nginx-1.9.9.tar.gz
    tar -zxvf nginx-1.9.9.tar.gz
    cd nginx-1.9.9

3.编译安装

    ./configure
    make
    make install
    whereis nginx  #默认安装路径是/usr/local/nginx

4.启动

    cd /usr/local/nginx/sbin
    ./nginx -h #查看帮助
    ./nginx  #启动
    ./nginx -s stop  #停止
    ./nginx -s reopen  #重启

5.链接到nginx命令,供全局访问

    ln -s /usr/local/nginx/sbin/nginx /usr/local/bin/nginx
    
**配置nginx**

*nginx的配置文件目录默认位于/usr/local/nginx/conf*

    cd /usr/local/nginx/conf
配置站点访问路径

    touch hexo.conf #创建hexo.conf
    vi hexo.conf #编辑hexo.conf文件

hexo.conf文件内容如下，location /表示用来配置根域名的访问路径

    location / {
      root /var/www/html/blog/public;
      index index.html;
    }

之后在nginx的主配置文件nginx.conf中引入hexo.conf，进入编辑模式vi nginx.conf

    server {
    	listen 80;
    	server_name www.yaotiancheng.cn yaotiancheng.cn;
    	include hexo.conf; #引入hexo.conf
    }

重新加载nginx,使配置生效
    
    nginx -s reload



**推送到服务器**

在本地hexo仓库中,打开配置文件_config.yml，修改deploy字段
    
    deploy:
      type: git
      message: 提交的信息
      repo: username@域名/ipadress:git仓库地址
      branch: master
*关于repo字段包含三个部分*

* username： 登陆服务器用户名, 一般为root
* 域名/ipdaress: 已解析的域名或者服务器ip地址
* git仓库地址: 此处为/opt/hexo.git

*这里需要注意的是服务器的ssh协议使用是22号端口号进行通信的。此处我们需要将服务器的端口号更改为默认值22。登陆服务器后修改配置文件。*

    vi /etc/ssh/sshd_config  #将Port字段为22
修改完成后需要重启ssh服务
    
    service sshd restart

同时,还需要在_config.yml文件中配置url字段和root字段,否则无法找到样式文件

    url: http://www.yaotiancheng.cn #主域名
    root: /
之后通过命令

    hexo g -d  
    #输入后会提示ssh密码 输入即可

即可将文件推送到服务器

打开浏览器, 输入网址，正常显示。

**Done!**
🙂

