---
title: 虚拟机进行jmeter分布式压测
date: 2020-08-22 15:05:23
tags:
- 知识点
- 虚拟机
- linux
- jmeter
---
<br>
### 【安装 jmeter】
> 安装java环境
 下载jmeter包，解压即可用 tar xf
 内存设置： jmeter.sh =>JVM_ARGS="-Xms512m -Xmx512m"
 
### 【分布式压测】
>    远程服务器(服务节点、压力机)：
        &emsp;&emsp;安装java 、jmeter
        &emsp;&emsp;配置：
            &emsp;&emsp;&emsp;&emsp;vim jmeter.properties               &emsp;&emsp;&emsp;&emsp;server.rmi.ssl.disable=true 修改为true
            &emsp;&emsp;&emsp;&emsp;vim system.properties               &emsp;&emsp;&emsp;&emsp;最后面添加java.rmi.server.hostname=本机ip
    本机(控制节点):
        &emsp;&emsp;安装java 、jmeter
        &emsp;&emsp;配置：
            &emsp;&emsp;&emsp;&emsp;vim jmeter.properties               &emsp;&emsp;&emsp;&emsp;server.rmi.ssl.disable=true 
            &emsp;&emsp;&emsp;&emsp;vim jmeter.properties               &emsp;&emsp;&emsp;&emsp;remote_hosts=负载机ip(多个可用逗号隔开)
### 【进行分布式压测】
> 压力机： ./jmeter-server 启动
    控制节点： run>remote start> 对应ip


