---
title: 面试-php1
date: 2020-02-26 23:12:07
tags:
- 面试
- 知识点
- php
---
1. Redis 秒杀实现

 redis队列（set）解决抢购高并发的原理：

> 在程序跟数据库之间, 利用redis队列做一个缓冲机制， 让所有用户端请求进
行排队， 先进先出原则(lpush rpop)

 - lpush -> 把用户的请求压入redis队列
 - rpop -> 守护进程，取队列中的数据，按照规定的抢购名额

 把多有点成功用户写入redis 并生成订单在lpush 中查看中奖的用户 并且及时给用户提示结果

2. 服务器定时器实现
>    分       小时   日   月  星期    命令

    0-59    0-23   1-31   1-12   0-6  command

30  7  8  *  *  ls   每月八号的七点半执行命令
*/15 * *  *  *  ls   每十五分钟执行一次命令,(机每小时的0 15 30 45 执行)
0  */2 *  *  *  ls  每两小时执行一次ls

注意：
- 星期中的0表示周日
- 每隔两小时的时候前面不能是* ，*会表示每分钟都会执行

第一种：crontab 在 etc/crontav 下设置 需要指定用户名

1、vim 命令进入/etc/crontab

2、在最后一行加入命令

3、重启crontab 使命令生效，service crond restart

第二种： crontab -e 

1、 添加命令

2、查看脚本是否有权限

3、查看命令所涉及到的文件是否有权限

4、重启 使生效

3. 结束死循环

1、 ctrl + c 结束
2、ps -ef | grep 名称 查询进程号
3、kill进程


4. 获取


