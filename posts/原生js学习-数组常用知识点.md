---
title: 原生js学习-----数组常用知识点
date: 2016-07-15 13:35:26
tags: [js]
---


原生js学习


<!-- more -->


JavaScript中的Array可以包含任意数据类型，并通过索引来访问每个元素。
#### 1. length，返回数组的长度

```
var array = [1,3,4,5];

alert(array.length);
```
#### 2. concat() 连接2个或多个数组，不会改变原数组，而是生成一个新数组

```
var arr1 = [1,2,3],
    arr2 = ['a','b','c'],
    arr3 = [4,5,6];

var arr4 = arr1.concat(arr2,arr3)
alert(arr4)
```
#### 3. join() 把当前Array的每个元素都用指定的字符串连接起来，然后返回连接后的字符串，原数组不变。

```
var arr = [1,2,3,'a','b'];

var arr2 = arr.join("-")

alert (arr2)
```
#### 4. pop() push() shift() unshift()

pop():    删除数组的最后一个元素 ，返回值为被删除的最后一个元素
shift():  删除数组的第一个元素 ，返回值为被删除的第一个元素
push():   向数组末尾添加若干个元素，返回值为添加完成后新数组的长度
unshift():向数组末尾添加若干个元素，返回值为添加完成后新数组的长度

```
var arr = [1,2,3,'a','b'];
arr.pop();
arr.shift();
arr.push(7,8,9);
arr.unshift('d','e','f')
```
#### 5. reverse() 反转整个原数组

```
var array = [1,2,3,'a'];
array.reverse();
```
#### 6. sort()  排序 .默认为字母编码顺序

```
var sortarr = [3,1,'a',2,5]
sortarr.sort();
```

> 如果想按其他标准进行排序，就需要提供比较函数，该函数比较2个值，然后返回一个用于说明这2个值的相对顺序的数字，比如比较a与b，返回值如下：  
> 若a小于b，在排序后的数组中a应该出现在b之前，则返回一个小于0的值。若a等于b，在排序后的数组中 a等于b 则返回0。若a大于b，则返回一个大于0的值。

```
array.sort(function(a,b) {
    return a-b
})
```
#### 7. slice(start,end)(注意不包括end位置) 对应字符串的处理函数 substring(),然后返回一个新的Array,原数组不变

```
var array12 = [1,3,4,5,6,7];
var newarr = array12.slice(1,5);
alert(newarr)
```
#### 8. toString() 将数组转为字符串

```
var array13 = [1,2,3,'a'];
alert(array13.toString());
```
#### 9. splice(index,howmany,newele1....,newelex) 从指定的索引开始删除若干元素，然后再从该位置添加若干元素，返回值为被删除的元素。

```
var names = ['a','b','c','d'];
var delnames = names.splice(0,2,'cc','dd');
alert(delnames+"\n"+names)
```
