---
title: Linux 三剑客-awk
date: 2020-06-17 11:53:42
tags:
- 知识点
- linux
- awk
---


AWK（数据切片）：统计相关数据，以及一定程度上代替grpe
    
>  awk 'BEGIN{ print "start" } pattern{ action } END{ print "end" }' file
>  awk 'pattern{action}'

- pattern:(找谁)
```text
    aek 'BEGIN{}END{}' 开始和结束
    awk '/pattern/' 正则匹配
    awk '/aa/, /bb/' 区间选择(两个选择以及之间的内容   )
    awk '$2~/pattern/' 单列字段匹配(从0开始)
    awk 'NR==2' 取第二行
	awk 'NR>1'去掉第一行

```
-  action:(干啥)


- 数据处理
```text
    $0 代表这一行
    $N 代表第N个字段
    $NF 代表最后一个字段

    RS=":" 以RS后面为分隔符,单行变多行  
    NR表示每一行的序号，NF表示这一行的字段数。
    计算行数要用 wc -l，END{print NR}也可用来输出行数

```

- 例子: 
```bash
    
    例子一:
 	ps | awk 'BEGIN{print "start"}{print $0}END{print "end"}'
    awk '/ 404 | 500 /' /tmp/nginx.log，
 	ps | awk 'NR>1'
 	ps | awk '{print $NF}'
    awk 'BEGIN{RS=":"}END{print NR}'     RS=":" 以RS后面为分隔符, NR行号
    awk '{print $NF}' 最后一个字段
    awk '{print $NF}' 倒数第二个字段
 	echo "123|456_789" | awk 'BEGIN{FS="\\||_"}{print $2}'
 	echo "123|456_789" | awk "BEGIN{FS=\"\\\\||_\"}{print \$2}" #尽量使用单引号
    例子三
 	echo $PATH | awk 'BEGIN{RS=":"}{print $0}' | grep -v "^$" | awk 'BEGIN{FS="\n";ORS=":"}{print $0}END{printf "\n" }'


```

- 数据计算
```bash
echo '1,10
 	2,20
 	3,30' | awk 'BEGIN{a=0;FS=","}{a+=$2}END{print a,a/NR}'
 	awk 'BEGIN{print 33*20*76/200/3}'
```
