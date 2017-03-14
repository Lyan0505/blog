---
title: ajax/getjson简单学习
date: 2016-09-11 17:18:26
tags: [jquery,ajax]
---

简单介绍下JSON以及jquery的ajax功能

<!-- more -->

#### 1. What is JSON?

简单地说，JSON就是一种数据格式。在这里，我就简单学习并介绍下如何使用HTTP请求（GET/POST/其他方法）来加载JSON数据。
#### 2. JSON jQuery 语法

如果不需要其他的功能，那么仅仅使用 $.getJSON()方法就可以非常方便的获取数据，从本质上说，它就是将$.ajax()的部分选项封装起来了，语法：

```
$.getJSON(url, data , success);

三个参数：url---一个字符串，其中包含了请求发送的地址
          data---可选参数，可以是一个对象或者一个被请求发送到服务器的字符串
          success---可选参数success(data,textStatus,jqXHR)，请求成功之后的回调函数
```

一般情况下，我们只关心返回的对象。这种情况下，成功的回调函数如下：

```
function success(data) {
    do something with data ,data is an object
}
```

同样的请求用$.ajax()触发是这样的：

```
$.ajax({
    dataType: 'json',
    url: url,
    data: data,
    success: success
})
```
#### 3. 更加常见的方法 $.ajax()

$.ajax()方法在任何情况下都是最根本的解决方法。选项很全面。async用于控制这个回调是不是和其他代码同时进行，如果为true，则同时，反之将阻止其他代码运行直到它下载完成。

```
$.ajax({
    type: 'GET',  //请求方式（post、get and 其他方法） 
    url: filename, //发送请求的地址
    data: data,   // 发送到服务器的数据
    async: false,   // Boolean类型的参数，默认为true
    cache: false,  //Boolean类型的参数，默认为true。当dataType为script时，默认为false，设置为false将不会从浏览器缓存中加载请求信息。
    beforeSend: function(xhr) {

    },
    // 发送请求前可以修改XMLHttpRequest对象的类型，例如添加自定义的HTTP头。如果返回的是false，则会取消本次ajax请求。xhr是唯一的一个参数。
    dataType: 'json', //  预期服务器返回的数据类型。(xml,html,script,json,jsonp,text)
    success: function(data,textStatus) {
        do something with the JSON data
    },
    //请求成功后的回调函数，data为返回数据，textStatus为描述状态的字符串
    complete: function(xhr,textStatus) {

    },
    //请求完成后的回调函数
    error: function(xhr,textStatus,errorThrown) {

    },
    //请求失败后的回调函数，第三个参数为捕获的错误对象。

})
```
#### 4.JSON验证

JSON有很严格的格式要求，不能有任何偏差。
