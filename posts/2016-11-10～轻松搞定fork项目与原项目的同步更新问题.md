---
title: 轻松搞定fork项目与原项目的同步更新问题
date: 2016-11-10 17:42:40
tags: [git]
---

工作中碰到，记录

<!-- more --> 


> 今天在工作中就碰到这样的一个问题，在fork的项目中提merge request，发现报错了，代码和原项目的代码不同步了，然后就自己查阅资料找到了解决方法，记录如下：(以我fork的任一项目为例)
### 1、git clone fork到自己仓库的项目

```
git clone git@github.com:arronf2e/newcomer.git
```
### 2、进入项目目录，并添加源分支地址到项目远程分支列表

```
cd newcomer
git remote add newcomer git@github.com:ShuyunXIANFESchool/newcomer.git
```
### 3、OK，第三步，fetch源分支到本地

```
git fetch newcomer
```
### 4、合并两个版本的代码

```
git merge newcomer/master
如果有冲突，部分会自动merge，部分需要自己手动merge冲突
```
### 5、push代码到我的fork仓库

```
git push origin master
```

![Blog icon](http://o9xap42x4.bkt.clouddn.com/1.jpg)
