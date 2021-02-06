---
title: BLog平台总结使用
date: 2020-02-17 00:14:38
tags:
- 资料
---


1.创建博客
> 安装nodejs（14版本会与hexo冲突）
> 安装hexo
> 在github上创建
> .....

2.如何在多台电脑上部署博客
> 创建仓库 https://github.com/en-one/en-one.github.io.git
> 创建两个分支：master 与 hexo；
> 设置hexo为默认分支（因为我们只需要手动管理这个分支上的Hexo网站文件）；
> 使用git clone 拷贝仓库
> 在本地博客文件夹下通过Git bash依次执行npm install hexo、hexo init、npm install 和 npm install hexo-deployer-git（此时当前分支应显示为hexo）;
> 修改_config.yml中的deploy参数，分支应为master；
> 依次执行git add .、git commit -m "..."、git push origin hexo提交网站相关的文件；
> 执行hexo g -d生成网站并部署到GitHub上。
这样一来，在GitHub上的en-one仓库就有两个分支，一个hexo分支用来存放网站的原始文件，一个master分支用来存放生成的静态网页。完美( •̀ ω •́ )y！


3.博客基础使用
> 1.依次执行git add .、git commit -m "..."、git push origin hexo指令将改动推送到GitHub（此时当前分支应为hexo）；
> 2.然后才执行hexo g -d发布网站到master分支上。

---

> 以上方法使用知乎大佬的方法
作者：CrazyMilk
链接：https://www.zhihu.com/question/21193762/answer/79109280
来源：知乎
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。