---
title: swoole重启报错Address already in use
date: 2020-07-20 17:44:30
tags:
- 知识点
- php
- swoole
---
 
<br>
### 【重启swoole 端口时发现端口被占用】

![Snipaste_2020-07-20_18-17-38.png](https://i.loli.net/2020/07/20/b9kiDcB7U6Xayos.png)



代码如下:
 
> netstat -anp | grep 端口号
      kill 端口号
      重启swoole项目

<br>

解决方法转载自：https://huanghantao.github.io/2017/07/02/bind-127-0-0-1-0-failed-Error-Address-already-in-use/