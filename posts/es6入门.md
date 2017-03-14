---
title: es6入门一
date: 2016-12-03 13:35:49
tags: [es6,javascript]
---

写篇博客记录一下自己学习es6的情况

<!-- more -->

#### 1. let 和 const 
> let和const都必须先声明后使用

    // let声明的变量只能在声明所处的代码块内有效,实现了块级作用域
    {
        let a = 1;
        var b = 2;
    }
    console.log(a);  // ReferenceError: a is not defined
    console.log(b);  // 2
    ----------------------------------------------------
    for循环的计数器，就很合适使用let命令
    var a = [];
    for( let i = 0; i < 5; i++) {
        a[i] = function() {
            console.log(i)
        }
    }
    a[2]();   // 2
    ----------------------------------------------------
    不存在变量提升,变量一定要在声明后使用，否则报错    == >暂时性死区 
    console.log(a); //ReferenceError
    console.log(b); //undefined
    let a = 1;
    var b = 2;

    ----------------------------------------------------
    不允许重复声明 ，也不能在函数内部重新声明参数，以下情况都会报错
    function t() {
        let a = 10;
        var a = 1;
    }
    function t() {
        let a = 10;
        let a = 1;
    }
    function t(arg) {
        let arg;
    }

    =====================================================
    // const 声明一个只读的常量。一旦声明，常量的值就不能改变，也实现了块级作用域
    const PI = 3.14159;
    PI = 3;
    console.log(PI)   // TypeError: Assignment to constant variable

    ----------------------------------------------------
    声明的时候必须初始化
    const PI ;  //SyntaxError: Missing initializer in const declaration

    ----------------------------------------------------
    与 let 一样，也不支持变量提升以及重复声明
    
#### 2. includes() startsWith() endsWith()  这三个方法都支持第二个参数，表示开始搜索的位置

> includes(): 返回布尔值，表示是否找到了参数字符串
> startsWith(): 返回布尔值，表示参数字符串是否在源字符串的头部
> endsWith(): 返回布尔值，表示参数字符串是否在源字符串的尾部

    let s = 'hello moto, I am arron';
    console.log(s.includes('hello')); // true
    console.log(s.startsWith('hello')); // true
    console.log(s.endsWith('arron')); // true
    console.log(s.startsWith('moto', 6)); // true
    'ARRON'.includes('RR')  // true

    数组实例的includes()
    let a = [1,23,4,5,6];
    console.log(a.includes(1))  // true
    console.log(a.includes(100)) // false

#### 3. 使用for of循环字符串或者数组

    let s = 'abcd';
    for(let c of s) {
        console.log(c)
    }
    a 
    b
    c
    d

    let arr = [1,2,3,4]
    for(let a of arr) {
        console.log(a)
    }
    1
    2
    3
    4

#### 4. Map和Set

    ...等待添加

#### 5. 模板字符串 ,特别适合用来做拼接字符串
    
    `` 为tab上面的键
    var s = {
        name: 'arron',
        age: 23
      }
    let str = `
    <li>hello,my name is ${s.name}</li>
    <li>I'm ${s.age} years old!</li>
    `
    console.log(str)  // <li>hello,my name is arron</li>
                         <li>I'm 23 years old!</li>

#### 6. 数组扩展 Array.from() 、 find() 、 findIndex()
    
> 1. Array.from() 
> 用于将两类对象转为真正的数组：类似数组的对象（array-like object）和可遍历（iterable）的对象（包括ES6新增的数据结构Set和Map）

    Array.from('abcd')  // ['a','b','c','d']

    function foo() {
        console.log(Array.from(arguments))  // [1,2,3,4,'ab']
    }
    foo(1,2,3,4,'ab')

    // DOM
    const foo = document.querySelectorAll('.foo');
    const nodes = Array.from(foo);

> 2. find()  用于找出第一个符合条件的数组元素

    [1,2,3,4,5].find((n)=> n>2)   // 3

> 3. findIndex()  用于找出第一个符合条件的数组元素下标 ，如果不存在，则返回 -1

    [1,2,3,4,5].findIndex((n)=> n>2)   // 2    

#### 7. 对象扩展

> 1. 简写,键值类同名的时候只需要写一个

    var arron= {
        name: name,
        say: function(){}
    }
    =====>  var arron = {name,say(){}}

> 2. Object.is() 比较两个值是否严格相等，与严格比较运算符（===）的行为基本一致

    Object.is('foo','foo')  // true
    Object.is(2,2)  // true

> 3. Object.assign() 用于对象的合并，将源对象（source）的所有可枚举属性，复制到目标对象（target) 浅拷贝,只是对源对象的引用 

    var t = {a:1};
    var s1 = {b:2};
    var s2 = {c:3};
    Object.assign(t,s1,s2)
    t // {a: 1, b: 2, c: 3}

    Object.assign([1, 2, 3], [4, 5])  // [4,5,3]

    !:  第一个参数为目标对象，后面的为源对象
        如果只有一个参数，直接返回该参数   Object.assign(t) === t
        如果参数不是对象，则会先转成对象，再返回
        由于null和undefined无法转为对象，所以用它们作为参数，会报错
        Object.assign(null) // error
        Object.assign(undefined) // error
    
    常见用途：
        为对象增加属性   Object.assign(this, {x:y})
        为对象添加方法
        克隆对象   Object.assign(object)
        合并多个对象
    
#### 7. 函数扩展

> 1. 可以给参数设置默认值

    function log(x, y = 'World') {
        console.log(x, y);  // undefined 'World'
    }
    ---------------------------------
    function Point(x = 0, y = 0) {
        this.x = x;
        this.y = y;
    }
    var p = new Point();

> 2. rest参数   可变参数，合成的是一个数组，可以传递或者不传递参数 或者传递无数个参数

    function t ( ...name ) {
        console.log(name)     // [1,2,3,4] 真正的数组，可以用数组的方法push....
    }
    t (1,2,3,4)

    注意：使用rest参数之后，不能再有任何其他参数，直接报错，rest只能作为最后一个参数
    function t(...name,a) {
         // 报错
    }

    function t( a, ...name) {
        console.log(a)   // 1
        console.log(name)  // [2,3,4]
    }
    t(1,2,3,4)

> 3. 扩展运算符 spread  ...  相当于rest参数的逆运算，将一个数组转为用逗号分隔的参数序列

    console.log(...[1,2,3])   // 1 2 3
    console.log(1,...[2,3,4],5) // 1 2 3 4 5
    Math.max(...[3,7,2])  // 7

> 4. 解构赋值 ( 数组 、对象)  本质上就是模式匹配,只要等号两边的模式相同,左边的变量就会被赋于相应的值,如果解构不成功,则值为undefined,不能对undefined和null进行解构

    var [a,b,c] = [1,2,3]
    console.log(a)  // 1
    console.log(b)  // 2
    console.log(c)  // 3

    var [,,third] = [1,2,3]
    console.log(third)  // 3

    var [f] = []
    console.log(f) // undefined

    var [f] = undefined   // 报错  Cannot read property 'Symbol(Symbol.iterator)' of undefined
    因为解构只用于数组或对象,其他类型变量都可以转为对象,但undefined和null不行

    //对象的解构赋值
    var {foo,bar} = {foo: 'foo', bar: 'bar'}
    console.log(foo)   // foo
    注意点: 左边的变量和右边的Key必须同名

    var { baz } = {foo: 'foo', bar: 'bar'}
    console.log(baz)   // undefined

    ...待继续更新   p26


