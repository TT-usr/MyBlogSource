---
title: 为hexo博客添加百度统计
date: 2017-02-20 17:44:51
tags:
---
**一、起因：**
    一直想知道自己网站的流量，最近没太多时间搞，发现其实百度统计挺简单的，先搞个文章记录一下吧。

**二、开始实施了**

1. 准备工作：
    
        注册百度统计，注册就不说啦。
        
2.查看代码咯：
    
    http://tongji.baidu.com/sc-web/home/site/getjs
    
3.复制代码：

    新建一个baidu_tongji.esj文件，将百度提供的代码帖进去保存，放在个性化的主题目录下 ./themes/主题名/layout/_partial/目录下

4.更改主题head.esj文件
    
    打开并添加一句 <%- partial('baidu_tongji') %>

5.接近尾声。
    
    命令行依次执行
    
    hexo clean
    
    hexo d

6.打开百度统计页面检测代码是否安装成功
   
    http://tongji.baidu.com/sc-web/home/js/check
    检测一下就好啦。

**三、最后**
其实没啥技术含量，只不过想写下来记录一下。




