---
title: 工作中常用git命令
date: 2019-03-13 19:06:05
tags: 
- git
- 知识点
---

> 前提：整理了一下工作中常用的基础git命令.
> 
> 主分支：master
> 本地开发分支 dev3.3.3
> 远程仓库分支 dev3.3.3
> 
> <!-- more -->

## 配置用户名

```bash
1、 配置用户名与邮箱
 git config --global user.name "用户名"
 git config --global user.email "用户邮箱"
2、查看用户名与邮箱
 git config --global user.name
 git config --global user.email
```

## 日常使用

1、拉取项目

```git
    git clone https://github.com/en-one/en-one.github.io.git
```

2、新建项目

```git
echo "# 我的项目" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/en-one/en-one.github.io.git
git push -u origin master
```

2、分支

```git
    git branch dev3.3.3     创建分支(本地)
    git branch -r           查看分支（r代表查看远程仓库分支）
    ①git fetch origin dev3.3.3(远程分支名):dev3.3.3(本地分支名)  远程分支拉取到本地，并创建本地分支
    ②git push --set-upstream-to=origin dev3.3.3 (本地当前分支为dev3.3.3)
    git checkout dev3.3.3    切换分支 
    git branch -d dev3.3.3    删除分支
```

3、内容合并（merge）

```git
    git checkout master     在本地开发环境为dev3.3.3版本
    git merge dev3.3.3      将dev3.3.3分支的修改合并到master分支上
    git push
```

4、提交(提交之前先 pull)

```git
    git pull
    git add  xxx(文件名，‘.’代表全部文件) 将内容添加到暂存区
    git commit -m "备注"    提交文件到暂存区
    git push                将暂存区内容推送到远程仓库
```

4、一些命令

```git
git status   显示工作目录和暂存区的状态
git log      显示commit的详细日志
```
