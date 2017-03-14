---
title: es6入门二
date: 2016-12-06 20:35:49
tags: [es6,javascript]
---

写篇博客记录一下自己学习es6的情况 ，续上篇

<!-- more -->

#### 1. 箭头函数 

> 函数体内的this对象，就是定义时所在的对象，而不是使用时所在的对象。，不可以当做构造函数，不可以使用arguments对象

    function s(n1,n2) {
        reutnr n1 + n2
    }
    ==> var s = ( n1, n2) => n1+n2
    当只有一句return语句的时候，可以省略 {}

#### 2. Set Map

    Set   数学中的集合，无重复值，是一个类数组，可以用 Array.from() 转化为一个真数组
    数组去重： Array.from(new Set([1,2,3,3,3,31,2,5]))

    Map  hash

#### 3. Promise  异步解决方案

#### 4. Module  模块化
    
    export default
    import