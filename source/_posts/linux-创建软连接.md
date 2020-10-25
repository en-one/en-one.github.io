---
title: linux 创建软连接
date: 2020-10-25 16:47:31
tags:
- 知识点
- linux
- 软连接
- 虚拟机
---
<br>

### 【创建软连接】
> ln file hfile    为file 创建一个硬连接hfile 
> ln -s file sfile 为file 创建一个软连接sfile
> - 硬链接可以随便转移到其他目录，软连接不行
> - 软连接标明文件属性，系统会自动识别为链接文件
> - 所有硬链接都必须位于同一分区，软连接可以位于不同分区

### 【红色闪烁的软连接】
> 现红色并且闪烁的文件和目录名通常是失效的链接，(的链接文件为B但是A丢了B还在)
> 出现问题：
>   &emsp;&emsp;ln -s file sfile 创建连接后为红色闪烁， 修改
>   &emsp;&emsp;ln -s /data/code/file sfile 修改目标文件为后，正常路径
> 颜色表示：
>   &emsp;&emsp;蓝色代表目录
>   &emsp;&emsp;绿色代表可执行文件
>   &emsp;&emsp;红色代表压缩文件
>   &emsp;&emsp;浅蓝色表示连接文件
>   &emsp;&emsp;灰色代表其他文件
>   &emsp;&emsp;黄色代表设备文件，包括block,char,fifo
>
### 【问题：“ln: 无法创建符号链接" ...... ": 不支持的操作”】
> 虚拟机共享windows文件夹,在共享的文件夹内,不可以创建到linux本地目录的链接.
  但可以在linux本地目录 创建到 共享目录的符号链接.
### 【借鉴文章连接】
> - https://blog.csdn.net/u011350541/article/details/53099625
> - https://blog.csdn.net/guozhongwei1/article/details/82834848

