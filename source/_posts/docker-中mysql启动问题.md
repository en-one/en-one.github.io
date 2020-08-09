---
title: docker 中mysql启动问题
date: 2020-08-04 21:37:17
tags:
- 虚拟机
- 知识点
- docker
- mysql
---
<br>
### 【MYSQL 服务无法启动，错误日志：InnoDB: .\ibdata1 must be writable】



【问题起因】：
    docker里面mysql镜像一直在重启，
    docker logs mysql5 查看原因
```bash
2020-08-04T17:14:56.155066Z 0 [ERROR] InnoDB: .\ibdata1 must be writable
2020-08-04T17:14:56.155066Z 0 [ERROR] InnoDB: The system tablespace must be writable
2020-08-04T17:14:56.375466Z 0 [ERROR] Plugin 'InnoDB' init function returned error.
2020-08-04T17:14:56.375466Z 0 [ERROR] Plugin 'InnoDB' registration as a STORAGE ENGINE failed.
2020-08-04T17:14:56.375466Z 0 [ERROR] Unknown/unsupported storage engine: InnoDB
2020-08-04T17:14:56.375466Z 0 [ERROR] Aborting
``` 
解决方法:
 
> 删除日志中的文件，打开mysql安装目录的data文件夹，删除以下2个文件：ib_logfile0和ib_logfile1

<br>
引自 https://blog.csdn.net/u012465296/article/details/71157286
