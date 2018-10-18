---
title: Less的使用
date: 2018-10-09 15:44:37
tags:
- less
categories:
- less
---
+ webstorm中配置less
  根据此路径File =》setting =》Tools =》File Watchers进入webstorm的less配置页面
  ![webpack](/images/less/less_setting.png)
  在new watcher界面中的program配置lessc.cmd的路径
  ![webpack](/images/less/less_watchers.png)
+ less嵌套规则
  ```python
  .container{
    h1{
         font-size: 25px;
         color:#E45456;
   }
    p{
         font-size: 25px;
         color:#3C7949;
    }

   .myclass{
    h1{
          font-size: 25px;
          color:#E45456;
    }
    p{
         font-size: 25px;
         color:#3C7949;
    }
   }
  }
  ```
+ less 操作
  LESS支持一些算术运算，例如加号(+),减号(-),乘法(*)和除法(/),它们可以对任何数字，颜色或变量进行操作。操作节省了大量的时间，当你使用变量，感觉就像是简单的数学工作。
  ```python
  @fontSize: 10px;
  .myclass {
   font-size: @fontSize * 2;
   color:green;
  }
  ```
+ Less 函数
  less映射具有值操作的javascript代码，并使用预定义的函数来操纵样式表中的HTML元素。它提供了操作颜色的几个功能，如圆函数，floor函数，ceil函数，百分比函数等。
  ```python
    @color:#FF8000;
    @width:1.0;
    .mycolor{
        color:@color;
        width:percentage(@width);
    }
  ```
+ Less 命名空间和访问器
  它用于将mixins分组，在通用名称下。使用命名空间可以避免名称冲突，并从外部封装mixin组。
  ```python
  .class1{
    .class2{
        .val(@param){
            font-size:@param;
            color:red;
        }
    }
  }
  .myclass{
    .class1 > .class2 > .val(20px);
  }
  ```
+ less变量范围
  变量范围指定可用变量的位置。变量将从本地作用域搜索，如果它们不可用，则编译器将从父作用域搜索。
  ```python
  @var:@a;
  @a:15px;
  .myclass{
    font-size:@var;
    @a:20px;
    color:green;
  }
  ```
+ less变量
  less变量除了可用属性值外，还能用于selector name，property name,url,@import statement
  + 用于selector name
  ```python
  @mySelector:banner;
  .@{mySelector}{
        font-weight:bold;
        line-height:40px;
        margin:0 auto;
  }
  ```
  + 用于peoperty name
  ```python
  @property:color;
  .widget{
    @{property}:#0ee;
    background-@{property}:#999;
  }
  ```
  + 用于url
  ```python
  @images:"../img";
  body{
  color:red;
  background:url("@{images}/white-sand.png");
  }
  ```
  + 变量的lazy loading
  ```python
  @var :0;
  .class{
    @var:1;
    .brass{
        @var:2;
        three:@var;
        @var:3;
    }
    one:@var;
  }
  ```
  编译后的结果：
  ```python
  .class{
    one:1;
  }
  class .brass{
    three:3;
  }
  ```
  one值为1，因为该处仅有可能访问的值为0和1的变量var，值为1的优先。three为3，因为此处可能访问到所有定义的变量var，值为2与3的var优先级较高，且值为3的var后定义，覆盖了值为2的var，最终使用的var值即为3.
+ less扩展
  Extend是一个LESS伪类，它通过使用:exten选择器在一个选择器中扩展其他选择器样式
  ```python
  h2 {
    &:extend(.style);
    font-style: italic;
  }
  .style {
    background: green;
  }
  ```
  输出的结果：
  ```python
  h2 {
    font-style: italic;
  }
  .style,
  h2 {
    background: green;
  }
  ```
+ Less 混合
  + 不带参数
  ```python
  @demo_width:300px;
  @demo_height:500px;
  @color_style:#E0EAFA;
  .border{
    border:2px solid red;
  }
  .box{
    width:@demo_width;
    height:@demo_height;
    background-color:@color_style;
    font-size:16px;
    margin:0 auto;
    .border;
  }
  ```
  执行后的结果：
  ```python
 .border{
    border:2px solid red;
 }
 .box{
    width:300px;
    height:500px;
    background-color:#e0eafa;
    font-size:16px;
    margin:0 auto;
    border:2px solid red;
 }
  ```
  + 带参数，无默认值
    可以传参数，参数可以写成一个变量，这样根据你的需要引用同一个类的样式，但传递参数不同，样式不同。
    ```python
     .border_test1(@border_width) {
        border: @border_width solid green;
     }
   ```
   ```python
   .box_test1 {
       .border_test1(1px);
        width: 100px;
        height: 200px;
        background-color: red;
    }
    .box_test2 {
        .border_test1(2px);
        width: 300px;
        height: 200px;
        background-color: yellow;
    }
   ```
  + 带参数，同时设置默认值
    相当于ES6语法中的设置变量，带参数默认值，如果有参数就使用参数，如果没有参数或者参数为undefined就使用默认值
    ```python
    .border_test2(@border_width: 10px) {
            border: @boeder_width solid pink;
    }
    ```
    ```python
     .box_text3 {
            .border_test2(5px);
            width: 200px;
            height: 100px;
     }
     ```
