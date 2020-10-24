---
title: hexo问题处理
date: 2020-10-24 17:42:16
tags:
- 知识点
- hexo问题处理
---

hexo d 部署时发生的问题，文件会正常上传，但是终端有error错误、

### 【"warning： LF will be replaced by CRLF"的去除方法】
>
>  git config --global core.autocrlf false

### 【fatal： master does not appear to be a git respository】
> 错误（hexo2.0写法）：
>&emsp;&emsp;deploy:
  &emsp;&emsp;&emsp;&emsp;type: git
  &emsp;&emsp;&emsp;&emsp;repo：
  &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;repository: https://github.com/en-one/en-one.github.io.git
  &emsp;&emsp;&emsp;&emsp; &emsp;&emsp;branch: master
>   正确：
>   &emsp;&emsp;deploy:
  &emsp;&emsp;&emsp;&emsp;type: git
  &emsp;&emsp;&emsp;&emsp;repository: https://github.com/en-one/en-one.github.io.git
  &emsp;&emsp;&emsp;&emsp;branch: master
