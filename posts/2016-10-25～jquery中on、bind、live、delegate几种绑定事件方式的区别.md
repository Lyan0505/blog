---
title: jquery中on、bind、live、delegate几种绑定事件方式的区别
date: 2016-10-25 17:38:24
tags: [jquery]
---

学习
<!-- more -->

> $(selector).bind(event,data,function)
> $(selector).live(event,data,function)//jquery1.9版本以下支持，jquery1.9及其以上版本删除了此方法，jquery1.9以上版本用on()方法来代替
> $(selector).delegate(childSelector,event,data,function)//jquery1.4.2及其以上版本；
> $(selector).on(event,childselector,data,function)//jquery1.7及其以上版本；jquery1.7版本出现之后用于替代bind()，live()绑定事件方式；
> 

### 0、live就算了，已经废弃了
### 1、bind  事件绑定到具体的元素上

```
$("#demo").bind('click', function(){
    alert("this is bind")
})
```
### 2、delegate 更精确的小范围使用事件代理，性能优于.live()。它不会把所有的event全部绑定到document,而是由你决定把它放在哪儿；可以用在动态添加的元素上。

```
$("parent").delegate('childselect', event, function() {

})
```
### 3、on 是最新的1.9版本整合了之前的三种方式的新事件绑定机制。.bind(), .live(), .delegate()都是通过.on()来实现的，.unbind(), .die(), .undelegate(),也是一样的都是通过.off()来实现的。

```
$('#parent').on("click", "child", function(){ 
    alert("Goodbye!");
});
```
