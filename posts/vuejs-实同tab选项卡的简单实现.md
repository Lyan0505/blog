---
title: vuejs——tab选项卡的简单实现
date: 2016-12-21 20:44:09
tags: [vuejs]
---

vuejs利用动态组件实现简单的tab选项卡 (1.0版本)

<!-- more -->

> 最近也在学习vuejs,并且手上一个项目也用到了这个框架,今天介绍一个简单实现tabs选项卡切换的方法。

#### 1. 嵌套路由实现

    <ul>
        <li v-link="{ path: '/class/child1'}">child1 tab</li>
        <li v-link="{ path: '/class/child2'}">child2 tab</li>
        <router-view></router-view>
    </ul>
    这个不是今天要重点记录的,略过啦-,-


#### 2. 利用vuejs的动态组件实现,官网介绍 [http://vuejs.org.cn/guide/components.html#动态组件](http://vuejs.org.cn/guide/components.html#动态组件)

    html:

    <div id="root">
      <ul>
        <li @click="toggle($index,tab.view)" v-for="tab in tabs" :class="{active: active == $index}">{{ tab.type }}</li>
      </ul>
      <br>
      <component :is="currentView" ></component>
    </div>

    script:

    Vue.component("child1", {
    	template: '<p>hell child1</p>'
    })
    Vue.component("child2", {
    	template: '<p>hell child2</p>'
    })
    new Vue({
      el: '#root',
      data: {
    		currentView: 'child1',
        active: 0,
        tabs: [
        	{
          	type: 'child1 tab',
            view: 'child1'
          },{
          	type: 'child2 tab',
            view: 'child2'
          }
        ]
    	},
      methods: {
      	toggle(i,v) {
          this.active = i
    	  this.currentView = v
    	}
      }

      css:
      .active {
        color: red;
        border-bottom: 1px solid red;
      }
      ul li {
        padding: 0 15px;
        float:left;
        list-style: none;
      }

在线预览: [https://jsfiddle.net/2kn4hqts/](https://jsfiddle.net/2kn4hqts/)

Good night !