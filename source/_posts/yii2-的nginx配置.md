---
title: yii2 的nginx配置
date: 2019-05-03 16:33:36
tags: 
- nginx
- 知识点
---

> mysite.conf 中一些注释
> <!--more-->

工作中使用的基于yii2的封装框架，下面是相应的nginx虚拟主机配置。

```nginx
server {
    charset utf-8;
    ## 上传大文件的容量（默认时1M）
    client_max_body_size 128M;

    ## 监听端口
    listen 80; 
    ## 域名可以有多个，用空格分开
    server_name mysite.test mysite2.test;
    ## root 指向项目根目录
    root        /path/to/basic/web;
    ## index 根目录下第一个解析的文件
    index       index.php;

    # rewrite重写功能，try_files按其后面的参数顺序检查文件是否存在，返回第一个找到的文件
     location / {
         try_files $uri $uri/ /index.php$is_args$args;
      }
    ## nginx 禁止访问.svn .git目录③
      location ~* /\.(ht|svn|git) {
          deny all;
      }
 
      location ~ .*\.php?$ {
          fastcgi_pass  unix:/tmp/php-cgi.sock; ## 监听端口①
          fastcgi_index index.php;
          include fastcgi.conf;
 
          limit_req zone=one burst=2 nodelay; ## 限流④
          limit_conn addr 2;
        
          ##  access_log 项目的接口访问日志
    	  ##  error_log 错误日志
          error_log   /path/to/basic/log/error.log;
          access_log  /data/web_logs/meet.log realip;
        
          # Project params②
          fastcgi_param ENV_MOD DEVELOPMENT; # 开发环境
          #fastcgi_param ENV_MOD TEST; # 测试环境
          #fastcgi_param ENV_MOD PRODUCTION; # 生产环境
      }
}
```



> ① Nginx 连接fastcgi的方式有两种：
> - TCP是使用TCP端口连接127.0.0.1:9000
> - Socket是使用unix domain socket连接套接字/dev/shm/php-cgi.sock（很多教程使用路径/tmp，而路径/dev/shm是个tmpfs，速度比磁盘快得多）
>   > fastcgi_pass  unix:/tmp/php-cgi.sock
>   > fastcgi_pass  127.0.0.1:9000
>
>   在服务器压力不大的情况下，tcp和socket差别不大，但在压力比较满的时候，用套接字方式，效果确实比较好。 

> ②  Nginx 设置环境变量
> - 在nginx的总体配置文件nginx.cong中
> - 在项目单独的nginx配置文件mysite.conf中

> ③ deny 命令
> - deny 表示不允许进行访问, 若不符合deny条件 ，则执行下一条指令
> - 从上到下执行，匹配到了便跳出

> ④限流
> - zone=one ：设置使用哪个配置区域来做限制
> - burst=2：(burst 爆发)，设置一个大小为2的缓冲区，担当有大量请求爆发的时候，超过了`访问频次`限制的请求，放在缓冲区，等待请求超过缓冲区大小，报503错误
> - nodelay：
>   - 若设置，会在瞬时提供处理（burst+rate）(rate单位r/s)个请求的能力，超过这个速度503错误，不会有请求等待的情况
>   - 未设置，所有请求依次排队等待
>
> - limit_conn addr 2： 指定addr这个地址只能同时存在两个链接