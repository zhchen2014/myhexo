title: GitHub管理博客源文件
tags:
  - github
  - hexo
categories: 技术宅 
date: 2015-06-11 10:45:08
---
#前言

<!--more-->

#步骤
1. 在GitHub下建立一个新的仓库，名字无所谓eg.myhexo
2. `cd`到本地需要用Git托管的文件夹，然后`git init`初始化git仓库，会生成`.git`文件夹
3. 在本地配置需要对应的git仓库
``` bash
$ git remote add orgin git@github.com:[yourusername]/myhexo.git
```
4. 配置仓库里哪些文件不需要托管，修改.gitignore文件，添加`public/`和`.deploy/`，原因请了解Hexo目录结构。
5. 使用命令完成推送
``` bash
$ git add .                    #提交当前目录所有文件到缓存区
$ git commit -m "提交的备注"   #缓存区文件提交到本地仓库    
$ git push origin master       #本地仓库文件push到origin对应的master位置
```
6. 日常同步备份




#Reference 
* [使用GitHub来管理博客源文件](http://wuchong.me/blog/2014/01/17/use-github-to-manage-hexo-source/)

