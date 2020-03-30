---
title: nginx + php-fpm 运行原理
date: 2019-07-28 23:33:04
tags:
- 知识点
---

一、 nginx 是什么
---
> Nginx ("engine x") 是一个高性能的HTTP和反向代理服务器，也是一个IMAP/POP3/SMTP服务器。

二、 php-fpm是什么
---
> - cgi : cgi协议，实现语言解释器与webwerver的通信。早期webserver只能处理html静态文件,按照cgi议去写，可以实现websever与动态语言的通信。如php-cgi程序。  
（缺点：webserver每收到一个请求，都要去去fork一个cgi进程，请求结束后再kill这个进程）
> -  fast-cgi: cgi协议改良版，每次处理完请求后，不会kill掉进程，而是保留这个进程，使这个进程可以一次处理多个请求。


> - php-fpm: (php-Fastcgi Process Manager),php-fpm是 FastCGI 的实现，并提供了进程管理的功能。  
> 进程包含master与worker两种进程:    
> master：只有一个，接收来自webserver的请求   
> worker：多个，每个进程内部都嵌入了一个php解释器，是php真正执行代码的地方



三、 nginx+php-fpm怎么工作
---