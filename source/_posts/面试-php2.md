---
title: 面试-php2
date: 2020-03-10 00:17:39
tags:
- 面试
- 知识点
- php
---
1. redis与memcached的异同，使用场景，数据类型，优缺点
2. 一次完整的http请求的过程，这个nginx是怎么处理的，php-fpm 是怎么处理的，怎么优化
- 一次php请求
```
 1. 本机浏览器中输入网址dev.meet.zjqq.mobi,请求发送到host指定的ip （默认127.0.0.1：：80），本机中配置的docker php 中的默认90端口
 2.监听默认端口的nginx收到此次请求，由于是http请求，nginx模块->http模块选择合适的handle模块 
 3. 
```
- 一次http请求
3. linux常用命令，查找文件的命令，find和which命令的区别
https://zhuanlan.zhihu.com/p/35727707
```
- which : 常用于查找可直接执行的命令，只能查找可执行文件
          基本只在$path下搜索，查找范围小 ，查找速度快
          默认返回第一个路径，-a返回全部
- whereis： 不止查找命令 其他文件类型都可以
            在path基础上增加了一些系统目录的查找，范围比which稍大，速度快
            -b限定只搜索二进制
- locate 超快速查找任意文件
            在linux内置的索引数据库查找，索引速度超快，新建文件需要一段时间加入索引库，updatedb强制更新索引
            返回大量选项，-r通过正则匹配
- find      任意文件
            直接搜索整个文件目录，默认从根目录开始，速度超慢
            -name指定文件名

```
4. 框架以及优缺点
5. 结合框架说明设计模式

