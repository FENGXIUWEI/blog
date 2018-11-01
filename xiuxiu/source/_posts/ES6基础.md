---
title: ES6基础
date: 2018-10-17 11:45:12
tags:
- ES6
categories:
- ES6
---
#### 变量声明const和let
  let表示变量，const表示常量。let和const都是块级作用域。
  与var不同，新的变量申明方式带来了一些不一样的特征，其中重要的两个特性就是提供了块级作用域和不在具备变量提升。
  ```python
  {
      let a = 20;
  }
  console.log(a);  // a is not defined
  ```
  编译后的结果
  ```python
   {
       let _a = 20;
   }

   console.log(a);  // a is not defined
    ```
#### 箭头函数的使用
+ 写法上面的不同
实例：对于函数未传递参数时，设置一个默认值
 ```python
 // 普通写法
 //存在问题，当传过来的值为0时
 function add(a,b){
    if(!b){
        b=100;
    }
    return a+b;
 }
 //es6的写法：
 function add（a，b=100）｛
    return a+b；
 ｝
 ```
 ```python
 function fn（a，...r）｛
 console.log（a，r）
 ｝
 r为剩余参数，一定要是参数的最后一个，否则会报错。
 箭头函数：
 var add=（a，b）=>｛
 return a+b；
 ｝
 注：a，b为参数，大括号中写的是方法。
 箭头函数：当参数为1个的时候可以省去（）小括号，当一个参数也没有时，不能省去小括号。当函数体中只有一个语句时可以省去｛｝中括号。
 ```
 + 箭头函数的特点
   + 1.箭头函数没有arguments获取实参的方法，想获取实参可以通过...r的方式获取实参。
   + 2.箭头函数中，没有this。如果你在箭头函数中使用了this，那么该this一定就是外层的this。也正是因为箭头函数中没有this，因此我们也就无从谈起用call/apply/bind来改变this指向
   + 3.箭头函数不能通过new的方法进行初始化

#### Promise
promise是异步编程得一种解决方案。
创建promise实例
```python
var p=new promise（（）=>｛｝）
//创建promise实例时，一定要写一个箭头函数，否则将会报错。
//promise创建实例时会同时生成两个参数，promisestatus，promisevalue。
//promise有三种状态：准备，成功，失败。
//promise的回调函数中传两个参数：resolve（成功），reject（失败）
```
promise外如何调用promise中的参数?
then中传递的参数就是promise通过resolve或者reject传递到外部的参数。
```python
p.then（（data）=>｛
console.log（"then："，data）
｝）
```
promise是构造函数，通过promise来构建一个异步任务处理对象。
resolve：函数，当我们调用函数的时候，可以把当前的promise对象的任务状态改成resolve；只要promise的任务状态发生了改变，这个promise对象的then方法就会被执行；then方法的第一个参数是resolve函数执行的，第二个参数是reject函数执行的;resolve和reject这两个函数是可以传入参数的，传入的参数将被传递给then中的函数进行使用；
promise任务链：then 函数执行后会返回一个新的promise对象;如果没有第一个then没有传入处理函数，那么会返回上一个处理状态的promise对象；如果then传入处理函数，那么默认返回一个fulfilled/resolve状态的promise对象；如果then传入了处理函数，通过处理函数显示的return了一个新promise，那么返回这个显示的promise；
promise存在问题：不易中途终止后续任务执行；
promise.all：将两个异步任务做完之后再执行下一个异步操作。
promise.race：前面两个异步任务，只要有一个执行完后，下面的异步就立刻开始执行；

