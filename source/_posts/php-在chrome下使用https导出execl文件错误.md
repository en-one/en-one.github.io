---
title: php 在chrome下使用https导出execl文件错误
date: 2019-05-20 19:57:34
tags:
- php
- https
- chrome
---

> 周一，一个天气晴朗的日子，然而线上产品却出了问题......
>
> <!--more-->

# PhpExecl 导出报错

正常操作：项目具有将数据库中信息以**execl**格式下载，是借助**Phpexecl**类 进行数据导出

问题描述：

1. 本地http情况下正常
2. 测试环境以及正式环境https下报错（如图）
3. chrome浏览器下报错，firefox正常

[![微信图片_20190523190156.png](https://i.loli.net/2019/05/23/5ce6810f0aa0954726.jpg)](https://i.loli.net/2019/05/23/5ce6810f0aa0954726.jpg)

解决方法：

1. 在PhpExecl类中的export函数中找到了header函数，删掉了函数中字符串中的空格

![](https://i.loli.net/2019/05/23/5ce680e6b0d0f25429.png)

2. 成功

问题解决过程：

1. 自我解决：以前由于对导出信息中的****特殊字符串**处理问题爆出过错误，打算以此入手
2. 前辈提示：由于生产环境问题比较紧急，问了前辈，提出怀疑是**header函数中是否有空格**导致错误
3. 找到对应函数，删掉其中的空格，成功
4. 在网上搜索了相关原理

> 大致情况是，header函数中的空格，被解析为%20，导致header函数无效，详细解释可以看下面链接


深入研究：<https://blog.csdn.net/qq_37118034/article/details/81945960>
