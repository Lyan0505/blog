---
title: windows7下git配置步骤详解
date: 2016-10-28 12:52:16
tags: [git]
---

本篇文章记录一下自己在window7下安装配置gib的过程

<!-- more -->

> Git是分布式的代码管理工具，远程的代码管理是基于SSH的，所以要使用远程的Git则需要SSH的配置.

#### 1.下载git for windows安装包：[https://git-for-windows.github.io](https://git-for-windows.github.io)
#### 2. 打开git bash ,设置Git的user name和email：

![git bash](http://7xtfps.com1.z0.glb.clouddn.com/gitbash.png)

```
$ git config --global user.name "yourname"  
$ git config --global user.email "youremail"
```
#### 3. 生成SSH密钥
1. 查看是否已经有了ssh密钥：cd ~/.ssh  
   如果没有密钥则不会有此文件夹，有则备份删除  
2. 生存密钥  
   
   `$ ssh-keygen -t rsa -C “youremail”`  
   
   按三个回车即可，最后得到了两个文件：id_rsa和id_rsa.pub
   
   ![ssh](http://7xtfps.com1.z0.glb.clouddn.com/ssh.png)
3. 查看并复制密钥
   
   `cat id_rsa.pub`  
   
   ![ssh](http://7xtfps.com1.z0.glb.clouddn.com/ssh2.png)
4. 进入github添加ssh-key
   
   进入github，点击如图的setting  
   
   ![github](http://7xtfps.com1.z0.glb.clouddn.com/github.png)
   
   点击左侧的 SSH and GPG keys  
   
   ![github2](http://7xtfps.com1.z0.glb.clouddn.com/github2.png)  
   
   接下来点击左上角的 New SSH keys  
   
   ![github3](http://7xtfps.com1.z0.glb.clouddn.com/github3.png)
   
   ![github4](http://7xtfps.com1.z0.glb.clouddn.com/github4.png)
   
   title 随便写,然后将刚才复制的密钥填入Key框，点击Add SSH Key 按钮即可完成。
5. 开始使用github
   
   接下来即可正常使用git各种命令，嗯，完美！
