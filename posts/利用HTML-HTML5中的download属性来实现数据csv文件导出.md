---
title: 利用HTML/HTML5中的download属性来实现数据csv文件导出
date: 2016-11-21 20:38:43
tags: [html,css]
---

纯前端实现文件的下载，将数据导出为csv文件。

<!-- more -->

> download 属性规定被下载的超链接目标。

#### 1. 基础写法
    <a href="url" download="filename">下载文件</a>
#### 2.浏览器兼容

![http://7xtfps.com1.z0.glb.clouddn.com/1.png](http://7xtfps.com1.z0.glb.clouddn.com/1.png)

    检测测当前浏览器是否支持download属性
    var isSupportDownload = 'download' in document.createElement('a');

#### 3. CSV： 逗号分隔值文件格式
> 文件以纯文本形式存储表格数据（数字和文本）。纯文本意味着该文件是一个字符序列，不含必须像二进制数字那样被解读的数据。CSV文件由任意数目的记录组成，记录间以某种换行符分隔；每条记录由字段组成，字段间的分隔符是其它字符或字符串，最常见的是逗号或制表符。通常，所有记录都有完全相同的字段序列。
其文件内容为以下内容  

    "#","姓名","照片","手机","性别","生日","会员卡种类","会员卡号"
    "1","arron","xxx","13890909090","male","930106","good","11809"
    "2","steven","xxx","13890908890","male","930206","good","11209"
    "3","jack","xxx","13890220090","male","930906","bad","11809"

> 实现原理：拼接字符串，生成csvstring，再利用a标签download的新属性实现csv文件的生成 


#### 4. 实践

    data:
    var people = [
        {
            "name": "Arron",
            "age: : "22",
            "sex" : "男",
            "birthday": "1993-01-06",
            "phone": "13187890289",
            "hobby": "basketball"
        },
        {
            "name": "Jack",
            "age: : "24",
            "sex" : "男",
            "birthday": "1991-02-22",
            "phone": "13567454389",
            "hobby": "football"
        },
        {
            "name": "Alice",
            "age: : "21",
            "sex" : "女",
            "birthday": "1996-11-26",
            "phone": "13187889509",
            "hobby": "reading"
        }
    ]

    code: 

    s1. 我们用一个数组来存一行数据,所以第一行用一个数组来保存字段名
    var head = [['name','age','sex','birthday','phone','hobby']];

    s2. 将数据push到大数组中
    var p = people;
    for(var i = 0 ; i < p.length; i++) {
        head.push([p[i].name, p[i].age, p[i].sex, p[i].birthday, p[i].phone, p[i].hobby]);
    }

    s3. 按照csv文件内容格式，把每个数组用 , 连接，形成一行，并存入新数组
    var csvRows = [];
    for(var i = 0 ; i < head.length; i++) {
        csvRows.push(head[i].join(','))
    }

    s4. 把新数组用 \n 回车连接，形成csvString

    var csvString = csvRows.join('\n');
    
    //BOM的方式解决EXCEL乱码问题
    var BOM = '\uFEFF';
    csvString = BOM + csvString;

    s5. 创建a标签
    var a = document.createElement('a');
    a.href = 'data:attachment/csv,' +  encodeURI(csvString);
    a.target = '_blank';
    a.download = 'info.csv';
    document.body.appendChild(a); // Firefox 中必须这么写，不然不会起效果
    a.click();
    document.body.removeChild(a);


[在线Demo](https://jsfiddle.net/upj5js7f/)

> 顺便说一下：关于文件的操作还是交给后端处理吧-，-


