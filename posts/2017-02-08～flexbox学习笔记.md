---
title: flexbox学习笔记
date: 2017-02-08 23:51:12
tags: [css]
---

flexbox布局学习

<!-- more -->

> Flexbox 布局是CSS3中一种新的布局模式，用于改进传统模式中标签对齐、方向、以及排序等等缺陷
浏览器支持情况:[http://caniuse.com/#feat=flexbox](http://caniuse.com/#feat=flexbox)


### 1. 开始使用

    //块flex元素
    
    <div class="container">
        <div class="item">item1</div>
        <div class="item">item2</div>
    </div>
    css
    .container {
        display: flex;
        display: -webkit-flex;    //Safari
    }

![http://o9xap42x4.bkt.clouddn.com/flex1.png](http://o9xap42x4.bkt.clouddn.com/flex1.png)

    //行内flex元素
    <div class="container">
      <div class="item">item1</div>
      <div class="item">item2</div>
    </div>
		<span>hello flexbox</span>
    css
    .container {
      display: inline-flex;
      display: -webkit-inline-flex;    //Safari
    }
![http://o9xap42x4.bkt.clouddn.com/flex2.png](http://o9xap42x4.bkt.clouddn.com/flex2.png)

### 2. 主轴和侧轴

![http://o9xap42x4.bkt.clouddn.com/flex3.png](http://o9xap42x4.bkt.clouddn.com/flex3.png)

### 3. flex-direction/-webkit-flex-direction   更改主轴方向

    row: 默认值，从左到右，从上到下 

![http://o9xap42x4.bkt.clouddn.com/flex22.png](http://o9xap42x4.bkt.clouddn.com/flex22.png)

    row-reverse: 主轴起点和终点交换位置 ， 从右往左  

![http://o9xap42x4.bkt.clouddn.com/flex44.png](http://o9xap42x4.bkt.clouddn.com/flex44.png)  

    column: 主轴与侧轴交换

![http://o9xap42x4.bkt.clouddn.com/flex55.png](http://o9xap42x4.bkt.clouddn.com/flex55.png)  

    column-reverse: 和column一样，方向相反

![http://o9xap42x4.bkt.clouddn.com/flex66.png](http://o9xap42x4.bkt.clouddn.com/flex66.png)

### 4. justify-content/-webkit-justify-content  主轴对齐

    flex-start(默认)：左对齐 

![http://o9xap42x4.bkt.clouddn.com/flexa1.png](http://o9xap42x4.bkt.clouddn.com/flexa1.png)

    flex-end：右对齐 

![http://o9xap42x4.bkt.clouddn.com/flexa2.png](http://o9xap42x4.bkt.clouddn.com/flexa2.png)

    center：居中

![http://o9xap42x4.bkt.clouddn.com/flexa3.png](http://o9xap42x4.bkt.clouddn.com/flexa3.png)


    space-between： 两端对齐，item之间的间隔都相等

![http://o9xap42x4.bkt.clouddn.com/flexa4.png](http://o9xap42x4.bkt.clouddn.com/flexa4.png)


    space-around：每个item两侧间隔相等

![http://o9xap42x4.bkt.clouddn.com/flexa5.png](http://o9xap42x4.bkt.clouddn.com/flexa5.png)

### 5. align-items/-webkit-align-items 侧轴对齐 

    flex-start

![http://o9xap42x4.bkt.clouddn.com/2161.png](http://o9xap42x4.bkt.clouddn.com/2161.png)

    flex-end

![http://o9xap42x4.bkt.clouddn.com/2162.png](http://o9xap42x4.bkt.clouddn.com/2162.png)

    center

![http://o9xap42x4.bkt.clouddn.com/2163.png](http://o9xap42x4.bkt.clouddn.com/2163.png)

    baseline: 以项目的第一行文字的基线对齐

![http://o9xap42x4.bkt.clouddn.com/2164.png](http://o9xap42x4.bkt.clouddn.com/2164.png)

    stretch(默认值): 当container不设置默认高度时，自动填满整个窗口的高度

![http://o9xap42x4.bkt.clouddn.com/2165.png](http://o9xap42x4.bkt.clouddn.com/2165.png)

### 6. flex-wrap/-webkit-flex-wrap 伸缩行换行

    nowrap(默认)：不换行

![http://o9xap42x4.bkt.clouddn.com/2166.png](http://o9xap42x4.bkt.clouddn.com/2166.png)

    wrap: 换行，第一排在上方，依次往下

![http://o9xap42x4.bkt.clouddn.com/2167.png](http://o9xap42x4.bkt.clouddn.com/2167.png)

    wrap-reverse:  换行，第一排在下方，依次往上

![http://o9xap42x4.bkt.clouddn.com/2168.png](http://o9xap42x4.bkt.clouddn.com/2168.png)

### 7. align-content/-webkit-align-content : 堆栈伸缩行，更改的flex-wrap的行为，对齐的不是项目，而是由flex-wrap产生的伸缩列

    stretch(默认): 轴线占满整个交叉轴

![http://o9xap42x4.bkt.clouddn.com/2169.png](http://o9xap42x4.bkt.clouddn.com/2169.png)

    flex-start: 与交叉轴起点对齐

![http://o9xap42x4.bkt.clouddn.com/21610.png](http://o9xap42x4.bkt.clouddn.com/21610.png)

    flex-end: 与交叉轴终点对齐 

![http://o9xap42x4.bkt.clouddn.com/21611.png](http://o9xap42x4.bkt.clouddn.com/21611.png)

    space-around: 每根轴线两侧距离都相等

![http://o9xap42x4.bkt.clouddn.com/21612.png](http://o9xap42x4.bkt.clouddn.com/21612.png)

    space-between：两端对齐

![http://o9xap42x4.bkt.clouddn.com/21613.png](http://o9xap42x4.bkt.clouddn.com/21613.png)

### 8. flex-flow/-webkit-flex-flow：伸缩方向与换行, flex-direction flex-wrap 的缩写

    flex-flow: [flex-direction] [flex-wrap]


> 上面介绍的都是父容器的一些属性，下面开始介绍一下flex item 的属性


### 9. flex-item 伸缩项目的属性

    order: 显示排列顺序，数值越小，排列越前，默认都为0

![http://o9xap42x4.bkt.clouddn.com/21614.png](http://o9xap42x4.bkt.clouddn.com/21614.png)


    margin: 外边距

    margin-right: auto

![http://o9xap42x4.bkt.clouddn.com/21615.png](http://o9xap42x4.bkt.clouddn.com/21615.png)

    margin: auto

![http://o9xap42x4.bkt.clouddn.com/21616.png](http://o9xap42x4.bkt.clouddn.com/21616.png)


    align-self: 侧轴对齐，属性和align-items一样，会覆盖父容器的align-items属性

![http://o9xap42x4.bkt.clouddn.com/21617.png](http://o9xap42x4.bkt.clouddn.com/21617.png)

    flex: [number]：该数字用于指定该项目所占用剩余空间比例

![http://o9xap42x4.bkt.clouddn.com/21618.png](http://o9xap42x4.bkt.clouddn.com/21618.png)
![http://o9xap42x4.bkt.clouddn.com/21619.png](http://o9xap42x4.bkt.clouddn.com/21619.png)