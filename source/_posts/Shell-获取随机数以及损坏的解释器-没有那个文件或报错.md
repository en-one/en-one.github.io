---
title: '“Shell 获取随机数” 以及 “损坏的解释器: 没有那个文件或报错”'
date: 2020-10-25 16:30:51
tags:
- 知识点
- shell
- 随机数
---
<br>

### 【在执行脚本时，弹出错误提示：/bin/sh^M：损坏的解释器: 没有那个文件或目录】
>
>  :set ff=unix
>   :wq

### 【shell 产生随机数方法】
```shell script
#方法一 内部系统变量（$RANDOM）
    #生成0-32767
        echo $RANDOM
    #生成400000~500000
        function rand(){   
            min=$1   
            max=$(($2-$min+1))   
            num=$(($RANDOM+1000000000)) #增加一个10位的数再求余   
            echo $(($num%$max+$min))   
        }   
         
        rnd=$(rand 400000 500000)   
        echo $rnd

#方法二 awk的随机函数
    awk 'BEGIN{srand();print rand()*1000000}'

#方法三 读取Linux的uuid码
    #UUID码全称是通用唯一识别码 (Universally Unique Identifier, UUID)，UUID格式是：包含32个16进制数字，以“-”连接号分为五段，形式为8-4-4-4-12的32个字符。linux的uuid码也是有内核提供的，在/proc/sys/kernel/random/uuid这个文件内。cat/proc/sys/kernel/random/uuid每次获取到的数据都会不同。
        function rand(){   
        min=$1   
        max=$(($2-$min+1))   
        num=$(cat /proc/sys/kernel/random/uuid | cksum | awk -F ' ' '{print $1}')   
        echo $(($num%$max+$min))   
        }   
         
        rnd=$(rand 100 500)   
        echo $rnd      
```