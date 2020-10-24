---
title: mysql 知识点
date: 2020-10-24 16:46:58
tags:
- 知识点
- mysql
- 测开
---
<br>

### 【mysql 语法】

>    【基础语法】
    &emsp;&emsp;插入数据 &emsp;&emsp;insert into 表名（字段1,字段2）values(值1，值2)
    &emsp;&emsp;删除数据 &emsp;&emsp;delete from 表名 where 字段名= 字段值
    &emsp;&emsp;更新    &emsp;&emsp;&emsp;&emsp;update 表名 set 字段1 = 值
>
>    &emsp;&emsp;复制表  &emsp;&emsp;&emsp;&emsp;create table stu_sch like stu;
    &emsp;&emsp;删除表中的数据    &emsp;&emsp;truncate table stu_n1;
>
>    【条件】
    &emsp;&emsp;WHERE子句：&emsp;&emsp;从数据源中去掉不符合其搜索条件的数据
    &emsp;&emsp;GROUP BY子句：&emsp;&emsp;搜集数据行到各个组中，统计函数为各个组计算统计值
    &emsp;&emsp;HAVING子句：&emsp;&emsp;去掉不符合其组搜索条件的各行数据行
>
>    【表连接】
    &emsp;&emsp;left join &emsp;&emsp;左外连接，左表记录会全部显示出来，而右表智会显示符合搜索条件的记录，没有的null
    &emsp;&emsp;roght join
    &emsp;&emsp;inner join &emsp;&emsp;内连接  显示交集
### 【mysql索引】
>    https://juejin.im/post/6844904126585765902#heading-0
### 【mysql explain】
### 【主键 外键 非空 唯一约束】
### 【索引 事务概念】
### 【redis】
>    list set hash zset string（最大512m）
    读110000/s ,写81000/s
    所有操作是原子性的，多个操作也支持事务
    支持订阅模式
### 【mongodb】
### 【neo4j】