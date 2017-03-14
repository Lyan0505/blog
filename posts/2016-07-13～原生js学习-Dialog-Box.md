---
title: '原生js学习-----Dialog Box '
date: 2016-07-13 14:34:50
tags: [js]
---


原生js学习


<!-- more -->

参考资料：妙味JS视频，百度网盘：[http://pan.baidu.com/s/1bKxhhG](http://pan.baidu.com/s/1bKxhhG) 密码：8mxd  
        javascript高级程序设计（第三版）：[http://pan.baidu.com/s/1c12If2g](http://pan.baidu.com/s/1c12If2g) 密码：tnnk
#### 1. alert()

> 显示带有一条指定消息和一个 OK 按钮的警告框

```
alert('hello alert');
```

![alert](http://7xtfps.com1.z0.glb.clouddn.com/alert.png)

没有返回值  

```
var a = alert("hello");
console.log(a)  //undefined
```
#### 2. confirm()

> 显示一个带有指定消息和OK及取消按钮的对话框

```
confirm("Are you Ready?")
```

![confirm](http://7xtfps.com1.z0.glb.clouddn.com/confirm1.png)

有返回值

```
var a = confirm("Are you Ready?")

如果点击确定，则 a = true
如果点击取消，则 a = false
```
#### 3. prompt()

> 显示可提示用户进行输入的对话框

```
prompt("what's your name?");
```

![prompt](http://7xtfps.com1.z0.glb.clouddn.com/prompt.png)

有返回值  

```
var txt = prompt("what's your name?");

则 txt = “输入的内容”
```
