---
title: vps实现文件下载
date: 2017-02-17 14:03:14
tags:
---

1.配置nginx配置文件

```shell
server {
        listen       8080;
        ##注意端口的占用问题
        server_name  域名;
        ##你的主机名或者是域名
        client_max_body_size 4G;
        ##文件限制大小
        root /opt/download/http;
        ##分配的路径
        location / {
		      autoindex on; ##显示索引
		      autoindex_exact_size on; ##显示大小
		      autoindex_localtime on;   ##显示时间
        }
    }
```
2.重新加载配置文件

```shell
##测试配置文件
 sudo /usr/sbin/nginx -t 
 
##重新加载配置文件
  sudo /etc/init.d/nginx reload
```

3.复制文件到服务器

```
scp 文件路径+文件名 用户@服务器:路径/文件
```

4.别人就可以下载啦，下载地址为：
https://www.yaotiancheng.cn:8080/文件路径/文件名

*文件路径为在你配置的/opt/download/http路径下的相对路径*


**写在最后：**
终于可以开心的用自己服务器的图床了，好开森，终于不用Google的图床导致未翻墙看不到图片啦~😊

