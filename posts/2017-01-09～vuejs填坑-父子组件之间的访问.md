---
title: vuejs填坑-父子组件之间的访问
date: 2017-01-09 00:22:59
tags: [vuejs]
---

工作中碰到，学习并记录

<!-- more -->

> 有时候我们需要父组件访问子组件，子组件访问父组件，或者是子组件访问根组件。

#### 1. 父组件访问子组件   $children或$ref

> $children  返回所有子组件的实例，是一个数组

	<div id="count">
		<button @click="showmsg">
	      显示两个组件的信息
	    </button>
			<child1></child1>
	    <child2></child2>
		</div>
	<template id="child1">
	  <div>
	    {{ msg }}
	  </div>
	</template>
	<template id="child2">
	  <div>
	    {{ msg }}
	  </div>
	</template>
	<script>
		Vue.component('child1', {
		  template: '#child1',
		  data () {
		    return {
		      msg: '这是子组件1的信息'
		    }
		  }
		})
		Vue.component('child2', {
		  template: '#child2',
		  data () {
		    return {
		      msg: '这是子组件2的信息'
		    }
		  }
		})
		new Vue({
		  el: '#count',
		  data: {
		    
		  },
		  methods: {
		    showmsg () {
		    	for(var i = 0; i < this.$children.length; i++) {
		      	alert(this.$children[i].msg)
		      }
		    }
		  }
		})
	</script>
[在线demo](https://jsfiddle.net/6rjb55qf/1/)

> $ref 有时候组件过多的话，就很记清各个组件的顺序与位置，所以通过给子组件一个索引ID

	<div id="count">
			<button @click="showmsg">
	      显示两个组件的信息
	    </button>
			<child1 ref='c1'></child1>
	    <child2 ref='c2'></child2>
		</div>
	<template id="child1">
	  <div>
	    {{ msg }}
	  </div>
	</template>
	<template id="child2">
	  <div>
	    {{ msg }}
	  </div>
	</template>
	<script>
		Vue.component('child1', {
		  template: '#child1',
		  data () {
		    return {
		      msg: '这是子组件1的信息'
		    }
		  }
		})
		Vue.component('child2', {
		  template: '#child2',
		  data () {
		    return {
		      msg: '这是子组件2的信息'
		    }
		  }
		})
		new Vue({
		  el: '#count',
		  data: {
		    
		  },
		  methods: {
		    showmsg () {
		    	alert(this.$refs.c1.msg)
		      alert(this.$refs.c2.msg)
		    }
		  }
		})
	</script>
[在线demo](https://jsfiddle.net/r8d1ka3q/1/)

#### 2. 子组件访问父组件 $parent

	<div id="count">
	    父组件中的msg: {{ msg }}
			<child1 ref='c1'></child1>
	    <child2 ref='c2'></child2>
		</div>
	<template id="child1">
	  <div>
	    {{ msg }}
	    <button @click="showpmsg">
	      显示父组件msg
	    </button>
	  </div>
	</template>
	<template id="child2">
	  <div>
	    {{ msg }}
	  </div>
	</template>
	<script>
		Vue.component('child1', {
		  template: '#child1',
		  data () {
		    return {
		      msg: '这是子组件1的信息'
		    }
		  },
		  methods: {
		  	showpmsg () {
					alert(this.$parent.msg)
		  	}
		  }
		})
		Vue.component('child2', {
		  template: '#child2',
		  data () {
		    return {
		      msg: '这是子组件2的信息'
		    }
		  }
		})
		new Vue({
		  el: '#count',
		  data: {
		    msg: 'hello parent'
		  }
		})
	</script>
[在线demo](https://jsfiddle.net/4raemhsj/1/)

#### 3. 子组件访问根组件 $root   当前组件树的根 Vue 实例。如果当前实例没有父实例，此实例将会是其自已。

	<div id="count">
	    父组件中的msg: {{ msg }}
			<child1 ref='c1'></child1>
	    <child2 ref='c2'></child2>
		</div>
	<template id="child1">
	  <div>
	    {{ msg }}
	    <cchild></cchild>
	  </div>
	</template>
	<template id="child2">
	  <div>
	    {{ msg }}
	  </div>
	</template>
	<template id="cchild">
	  <div>
	    <button @click="showroot">
	      showrootmsg
	    </button>
	  </div>
	</template>
	<script>
		Vue.component('child1', {
		  template: '#child1',
		  data () {
		    return {
		      msg: '这是子组件1的信息'
		    }
		  },
		  methods: {
		  	showpmsg () {
					alert(this.$parent.msg)
		  	}
		  }
		})
		Vue.component('child2', {
		  template: '#child2',
		  data () {
		    return {
		      msg: '这是子组件2的信息'
		    }
		  }
		})
		Vue.component('cchild', {
		  template: '#cchild',
		  data () {
		    return {
		      msg: '这是子组件1的信息'
		    }
		  },
		  methods: {
		  	showroot () {
					alert(this.$root.msg)
		  	}
		  }
		})
		new Vue({
		  el: '#count',
		  data: {
		    msg: 'hello root'
		  }
		})
	</script>

[在线demo](https://jsfiddle.net/0scmwfhy/1/)

Done! 1点了，晚安！


