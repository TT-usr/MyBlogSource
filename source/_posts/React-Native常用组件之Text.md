---
title: React-Native常用组件之Text
date: 2017-02-17 17:22:52
tags:
---

**一、什么是Text组件？**
        一个用于显示文本的`React`组件，和`Android`中的`TextView`组件或者`OC`中的`Label`组件相类似，专门用来显示基本的文本信息；除了基本的显示布局之外，可以进行嵌套显示，设置样式，以及可以做事件(例如:点击)处理；

**二、Text组件常用的属性方法**

```JavaScript
Attributes.style = {
    #字体颜色
    color string
    #进行设置Text显示文本的行数，如果显示的内容超过了行数，默认其他多余的信息就不会显示了
    containerBackgroundColor string
    #字体名称
    fontFamily string
    #字体大小
    fontSize number
    #字体风格
    fontStyle enum('normal', 'italic')
    #字体粗细权重
    fontWeight enum("normal", 'bold', '100', '200', '300', '400', '500', '600', '700', '800', '900')
    lineHeight number
    文本对其方式
    textAlign enum("auto", 'left', 'right', 'center')
    #文本方向
    writingDirection enum("auto", 'ltr', 'rtl')
    #行数
    numberOfLines number    
    #该方法当文本发生点击的时候调用该方法
    onPress  fcuntion
    #设置阴影效果
    textShadowOffset{width: number, height: number}
    #阴影效果圆角
    textShadowRadius number
    #阴影效果的颜色
    textShadowColor string
    #字符间距
    letterSpacing number
    #横线位置
    textDecorationLine  ("none", 'underline', 'line-through', 'underline line-through')
    #横线位置
    ("solid", 'double', 'dotted', 'dashed')
    #线的颜色
    textDecorationColor string
 }
```

**三、Text组件中样式的继承**

    对于Text元素里边的Text元素，其实是能够继承的,但是在React-native中是没有样式继承这种说法的

