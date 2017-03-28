---
title: osx环境下react-native android 开发环境的搭建
date: 2017-03-28 19:46:47  
tags: [react-native]
---

环境搭建步骤与所遇到问题的解决

<!-- more -->
> 安装 brew , nodejs 这些这篇就略过了，重点放在react-native上

### 1. 安装React Native的命令行工具（react-native-cli）

	npm install -g react-native-cli

如果你看到EACCES: permission denied这样的权限报错，执行以下命令修复，然后再重新执行上面的命令

	sudo chown -R `whoami` /usr/local

### 2. 下载Android Studio，目前需要Android Studio2.0或更高版本，Android Studio包含了运行和测试React Native应用所需的Android SDK和模拟器;Android Studio需要Java Development Kit [JDK] 1.8或更高版本。你可以在命令行中输入 javac -version来查看你当前安装的JDK版本。如果版本不合要求，则可以到官网上下载。

Android Studio下载地址： [https://developer.android.com/studio/index.html](https://developer.android.com/studio/index.html)

JDK版本不对的，可以到以下地址重新下载：[http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)

这部分详细可以查看官网介绍： [https://reactnative.cn/docs/0.42/getting-started.html](https://reactnative.cn/docs/0.42/getting-started.html)

### 3. Genymotion   ----- >   OK,这部分以上的内容都可以由以上地址查看，接下来主要说Genymotion的安装与启动

下载地址(需要先注册)：[https://www.genymotion.com/download/](https://www.genymotion.com/download/)

下载完之后按步骤安装，OK，以下是安装完成，我们打开Genymotion，看到以下界面：  

![http://o9xap42x4.bkt.clouddn.com/328a.png](http://o9xap42x4.bkt.clouddn.com/328a.png)  

我们先点击setting，在ADB标签下填下自己本地android SDK的正确地址，然后退出setting

![http://o9xap42x4.bkt.clouddn.com/328b.png](http://o9xap42x4.bkt.clouddn.com/328b.png) 

然后我们点击Add，在Available virtual devices选择你想用的任意一种虚拟设备，点击next  

![http://o9xap42x4.bkt.clouddn.com/328c.png](http://o9xap42x4.bkt.clouddn.com/328c.png)   
![http://o9xap42x4.bkt.clouddn.com/328d.png](http://o9xap42x4.bkt.clouddn.com/328d.png) 

继续点击next，就会安装相关程序，最后安装成功的界面  

![http://o9xap42x4.bkt.clouddn.com/328e.png](http://o9xap42x4.bkt.clouddn.com/328e.png) 

点击Finish，进入以下界面选中我们创建的虚拟设备并点击Start

![http://o9xap42x4.bkt.clouddn.com/328f.png](http://o9xap42x4.bkt.clouddn.com/328f.png)  
 
OK，这时候报错出现了，如下  

![http://o9xap42x4.bkt.clouddn.com/328g.png](http://o9xap42x4.bkt.clouddn.com/328g.png)  

查了下原因，分配的内存太大了，接下来我们去VirtualBox中修改该设备分配到的内存  

![http://o9xap42x4.bkt.clouddn.com/328h.png](http://o9xap42x4.bkt.clouddn.com/328h.png)  

在该页面中选中设备上右击选择设置，进入以下页面  

![http://o9xap42x4.bkt.clouddn.com/328i.png](http://o9xap42x4.bkt.clouddn.com/328i.png)  

我们在系统标签下，将内存大小调成1024M，点击保存后退出  

![http://o9xap42x4.bkt.clouddn.com/328j.png](http://o9xap42x4.bkt.clouddn.com/328j.png)  

接下来再去Genymotion中重新start该设备，发现成功了，一个安卓模拟器就跑起来了  

![http://o9xap42x4.bkt.clouddn.com/328k.png](http://o9xap42x4.bkt.clouddn.com/328k.png)  


### 4. 测试安装

	react-native init AwesomeProject
	cd AwesomeProject
	react-native run-android

成功界面如下：  
![http://o9xap42x4.bkt.clouddn.com/328z.png](http://o9xap42x4.bkt.clouddn.com/328z.png)  

Good Night!


