---
title: LInux与bash知识点
date: 2020-09-22 22:27:28
tags:
- 知识点
---
<br>
###  【文件】
>    命令：
        &emsp;&emsp;ls cd pwd mkdir rmdir cp rm mv
    文件属性：
        &emsp;&emsp;drwxr-xr-x  &emsp;2   &emsp;root    &emsp;root     &emsp;1320    02-24 17：44    install.log
        &emsp;&emsp;权限属性    &emsp;&emsp;连接  所有者    用户组   大小     修改内容            文件以及目录名
        &emsp;&emsp;d rwx r-x r-x
        &emsp;&emsp;文件类型 d 目录   - 文件    l 链接文件  b 设备文件 c 串行端口设备，如键盘鼠标
        &emsp;&emsp;rwx 拥有者
        &emsp;&emsp;r-x 所属组
        &emsp;&emsp;r-x 其他人
        修改文件属性：
        &emsp;&emsp;r 读权限read 4
        &emsp;&emsp;w 写权限write 2
        &emsp;&emsp;x 操作权限execute ``
        &emsp;&emsp;chmod 777 test 修改test文件属性
        &emsp;&emsp;df -h 显示磁盘大小

###  【网络】
>    ping 测试网络连接情况
        &emsp;&emsp;-c ping的次数
        &emsp;&emsp;-l  每次ping的时间间隔
    netstat 打印linux网络系统的状态信息
        &emsp;&emsp;-t 所有tcp
        &emsp;&emsp;-u 所有udp
        &emsp;&emsp;-l 只显示监听端口
        &emsp;&emsp;-n 以数字形式显示地址和端口号
        &emsp;&emsp;-p 显示i昵称的pid和名字
### 【性能】
>    top： 持续监视系统性能
    ps 查看进程信息
        &emsp;&emsp;-aux 显示所有进程 包括用户 分组情况

###  【Linux三剑客 grep awk sed】
###  【bash编程】
>    -gt 大于
    -ly 小于
    循环：
        &emsp;&emsp;for ... in ;do command1; done
        &emsp;&emsp;if [];then command1;elif[];then command2;fi
    脚本参数传递
        &emsp;&emsp;$0      &emsp;&emsp;脚本名称
        &emsp;&emsp;$1~$n   &emsp;&emsp;获取参数
        &emsp;&emsp;$#      &emsp;&emsp;传递到脚本的参数个数
        &emsp;&emsp;$$      &emsp;&emsp;脚本运行的当前进程id号
        &emsp;&emsp;$*      &emsp;&emsp;以一个但字符串显示所有向脚本传递的参数
        &emsp;&emsp;$?       &emsp;&emsp;显示最后命令的退出状态。0表述没有错误


### 【一键搭建web网站】
>    python2 -m CGIHTTPServer 80000
    python3 -m http.server 8000

### 【shell 小知识】
>    echo $a         会把\n转换为空格
    exho "$a"       显示原格式
     
