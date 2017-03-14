---
title: mac下通过XMAPP和phpstorm配置PHP开发环境
date: 2016-12-08 23:56:06
tags: [mac,php,后端]
---

新手使用xampp+phpstorm配置php开发环境的介绍

<!-- more -->

#### 1. 准备工作

> XAMPP是完全免费且易于安装的Apache发行版，其中包含MariaDB、PHP和Perl。 [XAMPP下载](https://www.apachefriends.org/zh_cn/index.html)  

------
> phpstorm PhpStorm is perfect for working with Symfony, Drupal, WordPress, Zend Framework, Laravel, Magento, Joomla!, CakePHP, Yii, and other frameworks. [phpstorm下载](https://www.jetbrains.com/phpstorm/)
	
#### 2. 软件安装

	基本都是傻瓜式安装，跟正常软件一样安装就可以了。略过

#### 3. 启动XAMPP

	XAMPP:  

	1. 直接运行应用程序中的 manager-osx 即可启动
	2. 命令行方式： sudo /Applications/XAMPP/xamppfiles/xampp start
	
> 启动正常提示  ![http://o9xap42x4.bkt.clouddn.com/xampp.png](http://o9xap42x4.bkt.clouddn.com/xampp.png)

	3. 注意如果提示 XAMPP:  Another web server is already running.  或者 上图中的 Apache web server  一直运行不起来

	执行： sudo apachectl stop   改下端口，这里我改了8089

	然后重新启动就可以了，这时候打开浏览器，输入: http://localhost:8089 ，出现以下画面说明启动完成。


> server启动成功  ![http://o9xap42x4.bkt.clouddn.com/success.png](http://o9xap42x4.bkt.clouddn.com/success.png)

#### 4. 配置phpstorm

	打开phpstorm ---> 点击 create new project ，然后将目录选择到上述设置中的XAMPP的根目录

> 此时还没有设置以上目录，右下角会有报错  ![http://o9xap42x4.bkt.clouddn.com/tip.png](http://o9xap42x4.bkt.clouddn.com/tip.png)

	解决方案

	点击左上角 phpstorm ---> Preferences ||  快捷键 "command + ," ，显示以下画面
> ![http://o9xap42x4.bkt.clouddn.com/storm1.png](http://o9xap42x4.bkt.clouddn.com/storm1.png)

	点击 no interpreter  后面的 ... 选择你的XMAPP路径即可
> ![http://o9xap42x4.bkt.clouddn.com/storm2.png](http://o9xap42x4.bkt.clouddn.com/storm2.png)

	点击 OK ,完成 ！ 现在编辑完php文件 ，再点击浏览器的预览，大功告成！


> 以上配置最大的坑是apache web server那一块，要特别注意啦 ！ 睡觉睡觉。 又 00：22分了，晚安-，- 


