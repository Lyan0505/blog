---
title: JSON.parse()和JSON.stringify()之间的区别
date: 2016-11-02 17:40:15
tags: [js]
---


JSON.parse() and JSON.stringify()
<!-- more -->

### parse用于从一个字符串中解析出json对象,比如

```
var arron = '{"name":"arron","age":23,"sex":"male"}';
JSON.parse(arron)    // Object   { name: "arron", age: 23, sex: "male"}
```
### stringify()用于从一个对象解析出字符串，比如

```
var oo  = {a:1,b:2}
JSON.stringify(oo)   //String   "{"a":1,"b":2}"
```

> 一直记不住，好记性不如烂键盘了，HEIHEIHEI
