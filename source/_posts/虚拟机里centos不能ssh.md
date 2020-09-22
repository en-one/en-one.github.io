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
  方法一：
    &emsp;&emsp;编辑=>虚拟网络编辑器=>还原默认设置
   方法二：
     &emsp;&emsp;控制面板 管理工具 服务 启动wm-dhcp以及vm-nat为自动(延迟) 状态
>  方法三：
        &emsp;&emsp;编辑=>虚拟网络编辑器=>桥接模式=>桥接到INternet开头=> service network restart 重启网络
            &emsp;&emsp;修改后发现虚拟机不能上网 vi /etc/resolv.conf，将namesever=8.8.8.8添加到文件中，然后重启网卡，

<br>
<br>
<br>
参考：https://zhidao.baidu.com/question/553464573715382812.html