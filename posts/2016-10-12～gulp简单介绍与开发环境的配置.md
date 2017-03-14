---
title: gulp简单介绍与开发环境的配置
date: 2016-10-12 17:37:29
tags: [gulp]
---

gulp初体验 

<!-- more -->

### 简介

一个前端自动化的构建工具，一个streaming构建工具，一个nodejs写的构建工具
好处：
1、js和css属于静态文件，很多时候浏览器存在缓存机制，为了避免缓存带来的误会，可以利用构建工具，给每一个静态文件添加一个版本号，这样浏览器就会认为是新的文件，就不存在缓存机制。
2、性能优化：文件合并，减少http请求；文件压缩，减少文件体积，加快下载速度；
3、效率提升：自动添加CSS3的前缀；代码分析检查改正
### 配置
#### 第一步：安装nodejs（此处省略，不会的google）
#### 第二步：全局安装gulp

```
npm i gulp -g
```
#### 第三步：创建项目文件夹，并初始化，再安装项目依赖

```
mkdir gulp-learning
cd gulp-learning
npm init
npm i gulp --save-dev
```
#### 第四步：创建gulp的配置文件gulpfile.js

```
touch gulpfile.js
```
#### 第五步：开始你的gulp之旅吧，创建第一个task

> gulpfile.js

```
var gulp = require('gulp');
gulp.task('default', function(){
    console.log('This is my first gulp task')
})
```
#### 第六步：终端中运行gulp命令

```
gulp / gulp default  (default为默认，可省略)
```
### OK，欢迎来到gulp的世界！
