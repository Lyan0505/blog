---
title: 如何在select标签中使用a标签跳转页面
date: 2016-08-22 13:09:34
tags: [css,html]
---

工作中碰到了这个需要，记录一下

<!--more-->
##### 1. 需求： 在select中想直接使用a标签跳转，错误想法

```
<select id="">
    <option>choose one</option>
    <option><a href="https://www.baidu.com">百度</a></option>
    <option><a href="https://www.qq.com">腾讯</a></option>
    <option><a href="https://www.360.com">360</a></option>
    <option><a href="https://http://www.mi.com/">小米</a></option>
</select>
```

  很遗憾，没有任何效果。  

2.正确解决方案

```
<select id="" onchange="window.location=this.value">
    <option>choose one</option>
    <option value="https://www.baidu.com">百度</option>
    <option value="https://www.qq.com">腾讯</option>
    <option value="https://www.360.com">360</option>
</select>
```

It's OK.
