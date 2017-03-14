---
title: vue填坑---在vuejs中实现a标签href tel的功能
date: 2016-12-29 14:37:34
tags: [vuejs]
---

工作中碰到，学习并记录

<!-- more -->

#### 1. 场景

    persons: [
        {
            name: 'arron',
            phone: 13811112222
        },{
            name: 'jack',
            phone: 13900088822
        },{
            name: 'steven',
            phone: 13711119909
        }
    ]
    遍历persons，实现tel功能

#### 2. 刚开始的错误想法

    <div v-for="p in persons">
        <p>
            name: {{ p.name }}
        </p>
        <p>
            tel: <a :href="tel: p.phone">call me</a>
        </p>
    </div>

    这时候发现这种写法根本无法实现tel的功能

#### 3. 正确做法，拼接字符串

    <div v-for="p in persons">
        <p>
            name: {{ p.name }}
        </p>
        <p>
            tel: <a :href="'tel:' + p.phone">call me</a>
        </p>
    </div>

OK! [Demo](https://jsfiddle.net/hpbub5c5/)
