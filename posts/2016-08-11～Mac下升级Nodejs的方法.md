---
title: Mac下升级Nodejs的方法
date: 2016-08-11 17:12:23
tags: [node]
---

mac nodejs升级

<!-- more -->
突然发现系统中的nodejs版本比较旧，想升级一下但又不想下载安装包一步一步安装， 发现还是可以很简单用命令行升级的。 

首先得清理npm的缓存  

```
sudo npm cache clean -f  
```

安装 n 包来升级nodejs  

```
sudo npm install -g n  
```

升级nodejs 到最新版本  

```
sudo n stable
```
