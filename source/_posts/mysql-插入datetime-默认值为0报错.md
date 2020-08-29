---
title: mysql 插入datetime 默认值为0报错
date: 2020-08-29 22:30:17
tags:
- 知识点
---
<br>

### 【mysql 插入datetime 默认值为0报错】
> 问题起因：
     &emsp;&emsp;用navicat导入数据时，报错:
    &emsp;&emsp;&emsp;&emsp;[Err] 1292 - Incorrect datetime value: '0000-00-00 00:00:00' for column 'CREATE_TIME' at row 1
> 影响：
     &emsp;&emsp;mysql版本不同，不支持datetime为0的情况。
>解决：
    &emsp;&emsp;select @@global.sql_mode;
     &emsp;&emsp;set @@global.sql_mode = 'STRICT_TRANS_TABLES,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION';   
