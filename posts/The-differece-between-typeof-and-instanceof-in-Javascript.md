---
title: The differece between typeof and instanceof in Javascript
date: 2016-11-12 17:46:47
tags: [js]
---

typeof instanceof

<!-- more -->


> JavaScript 中 typeof 和 instanceof 常用来判断一个变量是否为空，或者是什么类型的。但它们之间还是有区别的  
typeof: 检测参数的类型，返回值为该参数的类型
instance: 检测前者是否为后者的实例，返回值为true/false

    var a = [];
    typeof a;   //Object
    a instanceof Array;  //true
    a instanceof Object; // true

      
    var b = 'test';
    typeof b; //String
    b instanceof String;  //false