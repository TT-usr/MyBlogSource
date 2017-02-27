---
title: 为你的博客添加音频和视频
date: 2017-02-22 16:40:16
tags:
    - hexo
    - music
---

<h2>给你的hexo博客添加音频和视频吧~</h2>
这里需要使用两个播放器插件
>hexo-tag-aplayer:https://github.com/grzhan/hexo-tag-aplayer#upstream-issue

>hexo-tag-dplayer:https://github.com/NextMoe/hexo-tag-dplayer

两款插件基于 [DIYgod](https://github.com/DIYgod) 编写的 html5 播放器 [APlayer](https://github.com/grzhan/hexo-tag-aplayer#upstream-issue) 和 [DPlayer](https://github.com/NextMoe/hexo-tag-dplayer) 开发。

首先安装两款插件

打开`iTerm`, `cd`到你的`hexo`目录
运行如下两条命令

```shell
npm install hexo-tag-dplayer --save

npm install hexo-tag-aplayer --save
```

安装成功后，在 `Markdown` 文档中添加 `APlayer` 和 `DPlayer` 标签即可

比如添加如下代码使用 `APlayer` 和 `DPlayer`：

```JavaScript
{% aplayer "wake" "Hillsong Young And Free" "http://www.yaotiancheng.cn:8080/wake.mp3" "autoplay" %}

{% dplayer "url=http://devtest.qiniudn.com/若能绽放光芒.mp4" "addition=https://dplayer.daoapp.io/bilibili?aid=4157142" "api=http://dplayer.donot.help/dplayerpy" "pic=http://devtest.qiniudn.com/若能绽放光芒.png" "id=2622668" "loop=yes" "theme=#FADFA3" "autoplay=false" "width=233px" %}

```

[APlayer](https://github.com/grzhan/hexo-tag-aplayer#upstream-issue) 和 [DPlayer](https://github.com/NextMoe/hexo-tag-dplayer) 具体参数设置可以参考 Github 项目主页，不过默认参数足够用了。

另外aplayer已支持list播放，具体实现看GitHub项目页吧~

具体效果，看下面就可以了👇

{% aplayer "wake" "Hillsong Young And Free" "http://www.yaotiancheng.cn:8080/wake.mp3" %}

{% dplayer "url=http://devtest.qiniudn.com/若能绽放光芒.mp4" "addition=https://dplayer.daoapp.io/bilibili?aid=4157142" "api=http://dplayer.donot.help/dplayerpy" "pic=http://devtest.qiniudn.com/若能绽放光芒.png" "id=2622668" "loop=yes" "theme=#FADFA3" "autoplay=false" "width=233px" %}


希望你能喜欢，😆

