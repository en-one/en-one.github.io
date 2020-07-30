---
title: Linux 三剑客-sed
date: 2020-06-17 11:53:51
tags:
- 知识点
- linux
- sed
---
SED：sed的主要功能是替换，类似于sql里面的update语句。

流编辑器，一次处理一行内容，处理时，把当前处理的行存储在临时缓冲区，成为“模式空间”，接着用sed命令处理缓冲区的内容，处理完成后，把缓冲区内容送往屏幕，读入下一行，不断重复，直到文件末尾
    	文件内容没有被改变，除非使用重定向存储输出或-i
    
>  sed [options] '[地址定界] command' file(s)

- option:
```text
	-n 		只打印匹配到的行
    -e		多点编辑
    -r		支持扩展的正则表达式
    -i 		直接将处理的结果写入文件
    -i.bak	再将结果写入文件前备份一份

```
-  地址定界:(正则表达式)
```text
    - 不给地址 :对全文进行处理
    - 单地址： 
        - # ：指定的行
        - /pattern/： 被此正则能够匹配到的每一行
    - 地址范围

      sed -n '1~2p'  只打印奇数行 （1~2 从第1行，一次加2行）
      sed -n '2~2p'  只打印偶数行
```
	
- command: 
```text
    - d 删除模式空间匹配的行，并立即启用下一轮循环
    - D 删除模板第一行
    - s 替换指定字符
    - g 标识行内全部替换
    - p 打印当前模式空间内容，追加到默认输出之后
    - a 在指定行后面追加文本，使用\n实现多行追加
    - i 在行前面插入文本
    - c 取代                 

```

- 例子: 
```bash
    例子一
    sed -e 4a\newline test.json   //在第四行前面添加“newline”
    sed -i '4d' test.json         //删除第四行 
    sed -n '/is/p' test.json      //搜索带有is的行并打印
    sed -n '/is/d' test.json      //搜索带有is的行并删除
    sed 's/world/josiah/g' test.json  //搜索并替换
    sed '2,5c No 2-5 number'      //将第2-5行的内容取代成为『No 2-5 number』
```