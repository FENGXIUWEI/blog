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
   
   
   11111111111111111111111111111111111

