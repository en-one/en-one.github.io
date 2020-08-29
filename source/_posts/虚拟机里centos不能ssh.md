---
title: 虚拟机里centos不能ssh
date: 2020-08-29 16:53:15
tags:
- 知识点
---
<br>

### 【虚拟机里centos不能ssh】
> 问题起因：
     &emsp;&emsp;最新安装了vm，安装了centos7，保持虚拟机挂起，电脑关机后，第二天开启后，不能进行ssh联通
  短暂解决：
    &emsp;&emsp;虚拟机不能ping通 --[文章](https://josiah.top/2020/08/虚拟机不能ping通/)
   解决：
     &emsp;&emsp;控制面板 管理工具 服务 启动wm-dhcp以及vm-nat为自动(延迟) 状态  

<br>
<br>
<br>
参考：https://zhidao.baidu.com/question/553464573715382812.html