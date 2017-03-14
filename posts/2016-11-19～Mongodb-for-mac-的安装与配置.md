---
title: Mongodb for mac 的安装与配置
date: 2016-11-19 10:12:17
tags: [mongodb]
---

osx系统中 mongodb的安装与使用

<!-- more -->

> 网上的教程很多，但我安装的时候碰到挺多麻烦的，所以用这篇文章来记录一下，方便下次翻阅。


### 1. 使用homebrew安装

	brew update
	brew install mongodb

	使用mongod命令启动数据库

### 2. 下载安装包安装（重点）

	下载：curl http://downloads.mongodb.org/osx/mongodb-osx-x86_64-2.4.<6 class="tgz"
	解压：tar -zxvf mongodb-osx-x86_64-2.4.6
	将解压的安装文件移动到你所喜欢的位置： 我将它移动到应用程序下的mongodb文件夹
	mv -n ~/Downloads/mongodb-osx-x86_64-2.4.6 ~/Applications/mongodb/

	在根目录/下创建 data/db 目录，用于放置mongodb数据，并且给该目录设置权限
	sudo mkdir -p /data/db
	sudo chown -R  你自己的用户名(此外有个空格) /data 

	启动mongodb服务
	cd Applications/mongodb/bin
	./mongod

	打开另一个终端窗口
	cd Applications/mongodb/bin
	./mongo
	即可操作数据库

### 3. mongodb可视化工具，推荐robomongo,官网地址：[https://robomongo.org/](https://robomongo.org/)

	1. 下载安装包
	2. 打开软件，选择create
	3. 修改name，默认端口27017不用改，点击保存就可以了

Done!
