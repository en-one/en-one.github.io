---
title: win10 部署docker下nmp环境-遇见问题
date: 2019-07-06 23:49:57
tags: docker
---
> 记录本人在win10 环境下使用docker部署php开发环境遇到问题
> 以下仅为本人所见所闻。
<!--more-->

 一、使用项目
 使用了github上**yeszao**的[一键部署脚本](https://www.awaimai.com/2120.html)

 二、遇见问题
   1. 镜像文件挂载时出现地址已存在问题
  ```
  error while creating mount source path 'host_mnt/e/env/dnmp/...': mkdir /host_mnt/e: file existed
  ```
  ![文件挂载失败](https://i.loli.net/2019/07/07/5d20c67c0e95242852.png)
  解决方法：
    win10 环境下，在setting>>shared Drives 进行文件重新挂载，应用后即可重启docker。错误消失。

   2. 启动mysql镜像时，报错。
   ```
    ERROR: for mysql  Cannot start service mysql: driver failed programming    external connectivity on endpoint docker_mysql_1 ......
    ERROR: Encountered errors while bringing up the project.
   ```
  解决方法：
    在github的issue中找到[解决方法](https://github.com/docker-library/mysql/issues/291).**注释掉了端口号** ：

    ```
        mysql:
        image: mysql:8
        volumes:
        - ./mysql8/conf.d:/etc/mysql/conf.d:rw
        - ./mysql8/data:/var/lib/mysql:rw
        environment:
        - MYSQL_ROOT_PASSWORD=qzd1989
        #  ports:
        #   - "3306:3306"
    ```
  后续麻烦:
    由于注释掉了端口号，后续再navicat中不能连接docker中数据库，所以，又取消了端口号的注释，再次运行也没有报错。（事实证明了我是个lowb）

