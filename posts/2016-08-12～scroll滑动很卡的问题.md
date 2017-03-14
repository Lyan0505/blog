---
title: scroll滑动很卡的问题
date: 2016-08-12 17:20:03
tags: [css,html,移动端]
---


移动端webview碰到的问题

<!-- more -->

#### 在手机端页面中，如果你对某个div或模块使用了overflow scroll 属性，那个在手机上滑动这个模块的时候会比较卡，很不流畅，用户体验很差，为了优化这样的问题，我们需要用到下面这段代码:

-webkit-overflow-scrolling: touch;

这段代码创建了带有硬件加速的系统级控件，效率很高;但是会消耗更多内存。

原理详情请看：[http://blog.csdn.net/hursing/article/details/9186199](http://blog.csdn.net/hursing/article/details/9186199)
