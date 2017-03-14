---
title: 原生js学习-----javascript DOM 操作
date: 2016-07-13 15:33:39
tags: [js]
---


原生js学习


<!-- more -->

参考资料：妙味JS视频，百度网盘：[http://pan.baidu.com/s/1bKxhhG](http://pan.baidu.com/s/1bKxhhG) 密码：8mxd  
        javascript高级程序设计（第三版）：[http://pan.baidu.com/s/1c12If2g](http://pan.baidu.com/s/1c12If2g) 密码：tnnk
#### 1. 创建dom元素

```
var p = document.createElement("tag");
```
#### 2. 获取dom元素
##### getElementById("id"),如果id在元素中不是唯一的,那么获得的将是第一个ID.

```
<p id="test1">hello getElementById</p>
<script>
    var p = document.getElementById("test1");
</script>
```
##### getElementsByName("name"),仅用于input radio checkbox等元素,返回名字为name的元素数组

```
<div name="test2">hello</div>
<input type="text" name="test2">
<script>
    var get = document.getElementsByName("test2");
    console.log(get.length)  // 2 (测试发现对div也是有效的，待再次检验)
</script>
```
##### getElementsByClassName("class"),返回class为ClassName的元素数组

```
<div class="test3">hello</div>
<input type="text" name="test3">
<script>
    var get = document.getElementsByClassName("test2");
    console.log(get.length)  // 2
</script>
```
##### getElementsByTagName("tag"),返回标签为xx的元素数组

```
<div class="test4">aa</div>
<input type="text" class="test4">
<input type="text" >
<script>
    var get = document.getElementsByTagName("input");
    console.log(get.length)  // 2
</script>
```
#### 3. 对dom元素的操作
##### appendChild(node)，向当前对象追加节点

```
<div id="test5"></div>
<script>
    var div = document.getElementById("test5");
    var p = document.createElement("p");
    p.innerHTML = "hello";
    div.appendChild(p);
</script>
```
##### removeChild(node)，移除当前节点的子节点,并返回节点 //注意空格文本节点

```
<ul id="test6">
    <li>a</li>
    <li>b</li>
    <li>c</li>
    <li>d</li>
</ul>

<button id="btn">remove childnode</button>

<script>
    var list=document.getElementById("test6");
    var btn = document.getElementById("btn");
    btn.onclick = function() {
        list.removeChild(list.childNodes[0]);
    }
</script>
```
##### insertBefore(newElment,targetElement)  在某已存在节点前插入新的节点

```
<p id="test7">hello insertBefore</p>
<script>
    var p = document.getElementById("test7");
    var newp = document.createElement("li");
    newp.innerHTML = "test7 demo"
    document.body.insertBefore(newp,p);
</script>
```
#### 4. dom元素的常用属性
##### childeNodes ， 返回所有子节点对象

```
<ul id="list">
  <li>a</li>
  <li>b</li>
  <li>c</li>
  <li>d</li>
  <li>e</li>
</ul>
<script>
    var list = document.getElementById("list");
    console.log(list.childNodes.length);  // 5 ,火狐下11，因为有空行
</script>
```
##### text ， 返回节点的文本内容

```
<p id="test">hello</p>
<script>
    var p = document.getElementById("p");
    console.log(p.text);  //hello
</script>
```
##### innerHTML ， 返回节点或向节点插入内容

```
<ul id="list">
  <li>a</li>
  <li>b</li>
</ul>

<p id="p"></p>
<script>
    var list = document.getElementById("list");
    var p = document.getElementById("p");
    console.log(list.innerHTML);  
    // 输出  <li>a</li><li>b</li>
    p.innerHTML = "hello innnerHTML";
</script>
```
##### style,这是一个极其重要的属性,可以获取并修改每个单独的样式.

```
<p id="p">hello style</p>
<script>
    var p = document.getElementById("p");
    p.style.color = "red";
</script>
```
##### firstChild,lastChild,nextSibling,previousSibling  返回第一个/最后一个/下一个兄弟/上一个兄弟节点  //火狐下使用：firstElementChild,lastElementChild,nextElementSibling,previousElementSibling

```
<div id="before">aaa</div>
<div id="test">
  <p>1</p>
  <p>2</p>
  <p>3</p>
  <p>4</p>
</div>
<div id="hello">bbb</div>
<script>
    var list = document.getElementById("test");
    console.log(list.firstChild);    // <p>1</p>
    console.log(list.lastChild);    // <p>4</p>
    console.log(list.nextSibling);  // <div id="hello">bbb</div>
    console.log(list.previousElementSibling); // <div id="before">aaa</div>
</script>
```
##### parentNode,nodeName   返回父节点对象  /   返回节点的HTML标记名称，使用英文的大写字母，如P, DIV

```
<div id="test">
  <p>1</p>
  <p>2</p>
  <p>3</p>
  <p>4</p>
</div>
<script>
    var list = document.getElementById("test");
    console.log(list.parentNode);  //body
    console.log(list.nodeName);   // DIV (一定要大写)
</script>
```
##### setAttribute/getAttribute/removeAttribute   设置/获取/删除dom元素的属性

```
<div id="test">hello attribute</div>
<script>
    var p = document.getElementById("test");
    p.setAttribute("class","test1");  // <div id="test" class="test1">hello attribute</div>
    console.log(p.getAttribute("class")); // test1
    p.removeAttribute("class");  // <div id="test">hello attribute</div>
</script>
```
