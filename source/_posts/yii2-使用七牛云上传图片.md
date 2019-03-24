---
title: yii2 使用七牛云上传图片
date: 2019-03-18 23:43:31
tags: php
---

> 使用七牛云作为图片服务器，主要分三步：
>
> - 注册七牛云
> - 配置七牛云
> - 使用七牛云
>
> <!--more-->

1. 第一步：注册七牛云

> 详情见七牛云官方手册-[快速入门](https://developer.qiniu.com/kodo/manual/1233/console-quickstart )

2. 第二步：yii2 环境下composer下载七牛云sdk，配置七牛云的相关文件。



- composer下载七牛云sdk后，在vendor文件夹下位置位置。

  ![](https://i.loli.net/2019/03/19/5c8fc1462f553.png)

- 配置相关参数

  - 配置在自己的controller（或者model）文件里

    ```php
    // ak sk 存在于 个人中心>密钥管理中
        const AK = '你的7牛 ak';
        const SK = '你的7牛 sk';
    // domain bucket 存在左侧控制台 队形存储中
        const DOMAIN = '域名（七牛云有默认三十天过期的测试域名）';
        const BUCKET = '创建存储空间是设置的空间名称';    
    ```

  - 配置在Qiniu.php中

    ``` php
        public $up_host = 'http://up-z0.qiniu.com';   //默认上传的地址
        
    ```

    > 







3. 第三步：在文件中使用七牛云作为图片服务器，上传以及下载。