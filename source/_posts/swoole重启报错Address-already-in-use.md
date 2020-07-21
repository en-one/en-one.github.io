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


<br>

### 【WARNING	swManager_check_exit_status: worker#93[pid=25260] abnormal exit, status=0, signal=9 】

![UIx3QO.png](https://s1.ax1x.com/2020/07/21/UIx3QO.png)


> 在测试环境使用root账号进行项目重启
> 之后使用发布系统进行发布 发现不能重启项目，报错误 如上
> 原因：
> 发布系统是www 权限，重新发布不能杀掉root用户的进程，报错进程强制终止