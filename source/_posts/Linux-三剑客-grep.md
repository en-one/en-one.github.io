---
title: Linux 三剑客-grep
date: 2020-06-17 11:53:20
tags:
- 知识点
- linux
- grep
---



GREP(数据查找定位)：用于过滤、搜索的特定字符，可使用正则
    
>  grep [option] pattern file
>  grep pattern -r dir/ 递归搜索

- option:
```text
	-A(-B,-C) n(行数)  显示匹配内容哪一行 以及该行之后(该行之前，该行前后)内容
	-c 			  统计匹配行数
	-E			  使用扩展正则表达式, egrep
	-f  		  从文件获取正则匹配
	-n 			  显示匹配的行号
	-i 			  忽略字符大小写差别
	-v			  显示不被正则匹配到的内容
	-o 			  仅显示匹配到的字符串
	-q 			  静默模式，不输出任何信息
	-w 			  匹配整个单词
```


-  pattern:(正则表达式)
	
- 例子: 
```bash
    例子一
    ps -ef  | grep bash //查找bash字符串
    echo "ABC" | grep -i  abc
    ps -ef | grep bash | grep -v grep
    echo "1234 7654" | grep -o "[0-9]4" 
    echo "1234 7654" | grep -oE "[0-9]4|76"
    例子二
    curl https://testerhome.com | grep -o 'http://[a-zA-Z0-9\.\-]*'
    例子三
    ps -ef | grep 'php-fpm' | grep -vE 'grep|master' | awk '{print $2}'

```