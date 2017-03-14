---
title: vue填坑-父子组件互相传值的问题
date: 2017-01-08 19:58:38
tags: [vuejs]
---

工作中碰到的一些问题以及解决方案整理

<!-- more -->

### 1. 父子传值  props	
> 所有的 props 都是单向往下的，父组件 property 更新会影响子组件的,反过来则不会;另外，每次父组件中对应属性发生改变，子组件中的所有 props 都会被更新为最新的值。所以在子组件中，不应该对 props 进行更改

	<div id="app">
		<p>{{ message }}</p>
		<input type="text" v-model="message">
		<child :msg="message"></child>
	</div>
	<template id="child">
		<p>从父组件传来的msg: {{ msg }}</p>
	</template>
	<script>
		Vue.component('child', {
			template: '#child',
			props: ['msg']
		})
		new Vue({
			el: '#app',
			data: {
				message: 'hello props'
			}
		})
	</script>
[在线demo](https://jsfiddle.net/17oj444o/1/)

### 2. 子组件向父组件传递数据   自定义事件

> 使用 v-on 
所有Vue实例都实现了Events接口，即：  通过 $on(eventName) 监听事件 ;  通过 $emit(eventName) 触发事件

	<div id="count">
		<p>{{ total }}</p>
		<count-btn v-on:add="incrementTotal"></count-btn>
		<count-btn v-on:add="incrementTotal"></count-btn>		
	</div>
	<template id="child">
		<div>
			<button @click="add">{{ count }}</button>
		</div>
	</template>
	<script>
		Vue.component('count-btn', {
			template: '#child',
			data () {
				return {
					count: 0
				}
			},
			methods: {
				add () {
					this.count++
					this.$emit('add')
				}
			}
		})
		new Vue({
			el: '#count',
			data: {
				total: 0
			},
			methods: {
				incrementTotal () {
					this.total++
				}
			}
		})
	</script>
[在线demo](https://jsfiddle.net/8od0fyno/2/)