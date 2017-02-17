---
title: React-Native踩坑之旅系列二：invariant violation:expected a component class,got[object object]
date: 2017-02-15 11:03:16
tags:
        - react-native
---

**错误提示**

![](https://lh3.googleusercontent.com/LqR0vg1I4S1-Xc4v6KTjWkFZehQDm2B2Gs_3WNYgP3LA7kWHVKiciUdjNZONFewu79uUl4KpqsrdYLghhYk0Zuj5VNnx1v6_a9UmkpEw51sbq5wESCX4VDbAu4TJV9B9Uk7jWFmBhkYK4gmt__91V8XP6Mixh3mfc-Va7gwcPK5N3CRiZUDyYmALoHO1Ah-17lGSwUmTT_12S-IofoMUkBoy_iryc5cxGO004A3u6wHjKzwsl7mOu38UukDDKjbSlx-UDm6ZskAvetlKRn7wtxlSqxKbkR7P4XmyBWg6s-R-Am9_ngvmpczSk0wU2yiFMyrIKWoWS9VCEfKy9YjiiSC8fPhBvr-QJs5dMgFf2TmQy_6PISo7pkCQfZeHrT8H6kxvisBItALZaQU_oo-IXMPKJ2ErC7WaXqVm2O1V9QlB30dI_P6b79yPaC0YZnqBWZwnckhxFPVYTvWGqVkvG8qEmkmSt2lHOdHFvWumqurQvdh2LDbytub9W-goP2rfTnaVOEK0Q8g3RDxVIHrXf39VWL2vEmKNy-pWwQEjoEGqXW3xME6l_N-lirtslGZssdAIAMv_W1ieWO9ple02g4vEqt3XxtP-lLNeg2swsJHfVQCW7g9y=w750-h1334-no)

**解决方案：**

创建自定义组件首字母要大写，否则会报错.（切记 切记。）


