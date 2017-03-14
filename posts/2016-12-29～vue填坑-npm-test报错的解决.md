---
title: vue填坑-npm test报错的解决
date: 2016-12-29 17:09:54
tags: [vuejs]
---


工作中碰到，学习并记录

<!-- more -->

#### 1. 场景---编写测试用例也并行测试

    npm test 

    报错信息：
    Starting selenium server... There was an error while starting the Selenium server:

    Exception in thread "main" java.lang.UnsupportedClassVersionError: org/openqa/grid/selenium/GridLauncher : Unsupported major.minor version 51.0
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClassCond(ClassLoader.java:637)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:621)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:141)
	at java.net.URLClassLoader.defineClass(URLClassLoader.java:283)
	at java.net.URLClassLoader.access$000(URLClassLoader.java:58)
	at java.net.URLClassLoader$1.run(URLClassLoader.java:197)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:247)

#### 2. 原因

    higher JDK during compile time and lower JDK during runtime , 电脑 JDK 版本低

#### 3. 解决方案

    更新电脑中的 JDK version ，最好到 JDK 7 或以上

OK!