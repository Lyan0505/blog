---
title: macaca自动化测试初体验-pc端测试
date: 2016-11-10 17:44:39
tags: [macaca,测试]
---


macaca自动化测试初体验

<!-- more -->


> Macaca是一套完整的自动化测试解决方案。由阿里巴巴公司开源  
> Github:[http://macacajs.github.io/macaca/](http://macacajs.github.io/macaca/)  
> Api: [https://macacajs.github.io/macaca-wd/](https://macacajs.github.io/macaca-wd/)

#### 特点：
1. 同时支持pc端和移动端(Android iOS)自动化测试。
2. 支持nodejs、java、python

本篇只介绍pc端自动化测试

##### 1.install macaca
1.安装nodejs(略过)  
2.安装macaca-cli  

	npm i macaca-cli -g
3.安装webdriver-client

	npm install webdriver-client -g
	
4.安装macaca-electron(macaca-electron是基于Electron开发的Macaca驱动，是Macaca驱动之一，之后可以改为chrome)

	npm install macaca-electron -g

##### 2.create test dir，测试脚本均放在macaca-test文件夹内
	mkdir macaca-test-dir
	cd macaca-test
	npm init
	npm install macaca-cli webdriver-client macaca-eletron --save
	mkdir macaca-test
	cd macaca-test 
	touch test1.js
	cd ..
	(sudo) macaca run --verbose