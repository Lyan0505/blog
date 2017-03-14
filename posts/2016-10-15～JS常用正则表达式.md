---
title: JS常用正则表达式
date: 2016-10-15 17:17:24
tags: [js]
---

collections

<!-- more -->

#### 1. 邮箱验证(ismail.test(val))

```
var ismail = /^\w+((-\w+)|(\.\w+))*\@[A-Za-z0-9]+((\.|-)[A-Za-z0-9]+)*\.[A-Za-z0-9]+$/;  
```
#### 2.手机号码验证 (isMobile.test(val))

```
var isMobile=/^(?:13\d|15\d|18\d)\d{5}(\d{3}|\*{3})$/;
```
#### 3.座机号码验证  (isPhone.test(val))

```
var isPhone=/^((0\d{2,3})-)?(\d{7,8})(-(\d{3,}))?$/;
```
#### 4.邮箱编码

```
/^[0-9]{6}$/.test(val)
```
#### 5.车牌号

```
/^[A-Za-z0-9]{6}$/.test(val)
```

本文出自 不羁虫，永久链接: [http://www.bujichong.com/m/61](http://www.bujichong.com/m/61)
