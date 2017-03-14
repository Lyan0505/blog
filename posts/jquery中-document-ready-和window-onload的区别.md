---
title: jquery中$(document).ready()和window.onload的区别
date: 2016-10-05 17:41:30
tags: [jquery]
---


学习
<!-- more -->

### 1、执行时间

window.onload 要等页面中的所有元素（包括图片）加载完成才执行；
$(document).ready() 是在dom结构绘制完毕就执行，不必等到加载完成。
### 2、编写的个数

window.onload 不能执行多个，前者会被后者覆盖；
$(document).ready() 可以写任意个，而且都会执行。
### 3、简写

window.onload 没有简写；
$(document).ready() 可以简写为$(function(){})
