---
title: python 实战知识点
date: 2020-06-28 22:49:15
tags:
- 知识点
- 测试开发
- python
---

1.基础

变量b里面引用a，使用“f”
a="aaa"
b=f"fsfdsfsf{a}"

2.数组切片 左闭右开

3.列表 --数组
元祖(一个星号解压缩)
 集合
  字典(两个星号解压缩)--对象

4.global 使变量在函数内可以被修改

5.文件读写  open close
with open('venv/pyvenv.cfg', 'rt') as f:
    # print(f.readlines())
    while True:
        line = f.readline()
        if line:
            print(line)
        else:
            break

6.json
json.dumps(python_obj) 吧数据类型转换成字符串
json.loads(json_string) 字符串转换成json
json.dump(json_string， open(file,'w'))  数据类型转换成字符串并存储在文件中
json.load(file_stream) 吧文件打开 把里面的字符串转换成数据类型
7.异常
try:
except:异常
else:不走异常
finally是否异常，都会走

raise EXceptio()抛出异常

8.进程 : 执行中的程序，拥有独立地址空间、内存 数据占
多线程并发执行--轮训
多进程并行

9.包引用
import　值传递
form　import引用传递

10 面对对象
__money 表示私有属性，实例以及子类不能访问，需要定义方法获取
dir(p)获取可以被访问的私有变量
类中的self 是实例，实例调用类里面的东西会默认传到第一个位置
在类的方法上面加@classmethod ，然后把self换成cls 可以用类名调用函数
super() 调用父类方法

