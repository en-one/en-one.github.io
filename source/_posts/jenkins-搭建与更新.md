---
title: jenkins 搭建与更新
date: 2020-10-24 18:07:33
tags:
- 知识点
- jenkins 
- 测开
---
<br>

### 【jenkins 搭建】

```jenkins
    version: '3'
    services:
      jenkins:
        image: 'jenkinsci/blueocean'
        container_name: 'jenkins'
        restart: always
        ports:
          - '8081:8080'
          - '50000:50000'
        environment:
          TZ: Asia/Shanghai
        volumes:
          - '/data/jenkins/data:/var/jenkins_home'
```
    
### 【搭建后启动时权限问题】
>   docker logs jenkins 发现权限问题
>   原因：
>   &emsp;&emsp;jenkins容器内部使用用户jenkins，外部分配权限是root，挂载文件时权限不够
>   解决方法：
>   &emsp;&emsp;1、docker-compose中添加 user：root 配置
>   &emsp;&emsp;2、新建jenkins用户，外部给jenkins文件夹分配jenkis

### 【linux 用户组】
> useradd jenkins 创建用户
> tail -1 /etc/passwd 查看用户信息
> 有关linux用户以及用户组  https://juejin.im/post/6844903862604824590#heading-2
### 【更新】
>   进入容器 docker exec -it jenkins bash
>   下载软件 wget url(jenkins提示更新时会有页面链接)，如果不能下载，通过挂载路径将本地下载的war包放到对应目录下
>   移动包   mv ./jenkins.war /usr/share/jenkins
>   修改权限 chmod 777 /usr/share/jenkins/jenkins.war
>   重启    docker restart jenkins

