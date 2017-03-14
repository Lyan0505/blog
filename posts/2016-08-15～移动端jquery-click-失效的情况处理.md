---
title: 移动端jquery click 失效的情况处理
date: 2016-08-15 12:28:36
tags: [css,html,移动端]
---

移动端webview碰到的问题

<!-- more -->

安卓失效，ios正常
最近在做一个移动端的小项目，突然就碰到这样一个坑，demo代码：  

```
<li>click me</li>
<p style="display none">show</p>
<script>
    $(function(){

        $("li").click(function() {

            $("p").show();

        })

    })
</script>
```

当时情况就是pc端 chrome模拟点击没有问题，Ios没有问题，安卓点击无效果。后来在群友的帮助下，发现一个很巧的方法：

```
style.css

li {
    cursor: pointer;
}
```

OK,完美解决点击问题
