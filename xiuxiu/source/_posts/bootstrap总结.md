---
title: bootstrap总结
date: 2018-09-26 15:20:52
tags:
- bootstrap
categories:
- bootstrap
---
### bootstrap 排版样式
+ 标题
  + 从 h1 到 h6
  ```python
  <h1>Bootstrap 排版</h1> //36px
  <h2>Bootstrap 排版</h2> //30px
  <h3>Bootstrap 排版</h3> //24px
  <h4>Bootstrap 排版</h4> //18px
  <h5>Bootstrap 排版</h5> //14px
  <h6>Bootstrap 排版</h6> //12px
  <h2>bootstrap课程</h2> <p class="lead">hello world</p>
  ```
+ 列表
  + 有序列表、无序列表、自定义列表
    + .list-unstyled
    + .list-inline
    + .dl-horizontal 应用于&lt;dl&gt;元素和&lt;dt&gt;元素中

+ 表格
  + 基本表格 `<table class="table">`
  + 条纹表格 `<table class="table table-striped">`
  + 边框表格 `<table class="table table-bordered">`
  + 悬停表格 `<table class="table table-hover">`
  + 精简表格 `<table class="table table-condensed">`
  + 状态表格active、success、info、warning、danger
  + 隐藏某一行 `<tr class="sr-only">`
  + 响应式表格
    + 表格父元素设置响应式，小于 768px 出现边框
      `<div class="table-responsive">`

+ 按钮
  + 按钮标签
    + 转化成普通按钮
    + `<a href="###" class="btn btn-default">Link</a>`
    + `<button class="btn btn-default">Button</button>`
    + `<input type="button" class="btn btn-default" value="input">`
    + 注意：为了跨浏览器展现，尽量使用`button`
  + 按钮大小
    + `.btn-lg` 这会让按钮看起来比较大。
    + `.btn-sm` 这会让按钮看起来比较小。
    + `.btn-xs` 这会让按钮看起来特别小。
  + 预定义样式
    + `.btn-default` 默认/标准按钮
    + `.btn-primary` 首选项样式
    + `.btn-success` 成功样式
    + `.btn-info` 一般信息样式
    + `.btn-warning` 警告样式
    + `.btn-danger` 危险样式
    + `.btn-link` 链接样式
  + 块级按钮
    + `.btn-block` 块级按钮(拉伸至父元素100%的宽度)
  + 激活状态
    + `<button class="btn active">Button</button>`
  + 禁用状态
    + `<button class="btn active disabled">Button</button>`

+ 图片
  + `.img-rounded` 圆角 (IE8 不支持)
  + `.img-circle` 圆形 (IE8 不支持)
  + `.img-thumbnail` 缩略图功能
  + `.img-responsive` 图片响应式 (将很好地扩展到父元素)

+ 栅格系统
  + 响应式网格系统随着屏幕或视口（viewport）尺寸的增加，系统会自动分为最多12列。
  + 工作原理
    + 行必须放置在.container(固定宽度)或者.container-fluid(100%宽度) class内，获得适当的对齐(alignment)和内边距(padding)
    + 内容放置在列中，唯有列可以是行的直接子元素
    + 预定义的网格类，比如 .row 和 .col-lg-4，可用于快速创建网格布局
    + 列通过内边距（padding）来创建列内容之间的间隙
  + 媒体查询
    + 超小设备（手机，小于 768px）
    + 小型设备（平板电脑，大于等于768px）`@media (min-width: @screen-sm-min) and (max-width: @screen-sm-max) { ... }`
    + 中型设备（台式电脑，大于等于992px）`@media (min-width: @screen-md-min) and (max-width: @screen-md-max) { ... }`
    + 大型设备（大台式电脑，大于等于1200px）`@media (min-width: @screen-lg-min) { ... }`
  + 栅格参数
    + 超小屏幕 手机 (<768px)
    + 小屏幕 平板 (≥768px)
    + 中等屏幕 桌面显示器 (≥992px)
    + 大屏幕 大桌面显示器 (≥1200px)
    + `.container` 最大宽度 None（自动）`750px 970px 1170px `
    + 类前缀 `.col-xs- .col-sm- .col-md- .col-lg-`

  + 四种屏幕分类全部激活
  ```python
  <div class="container">
      <div class="row">
          <div class="col-lg-3 col-md-4 col-sm-6 col-xs-12 a">4</div>
          <div class="col-lg-3 col-md-4 col-sm-6 col-xs-12 a">4</div>
          <div class="col-lg-3 col-md-4 col-sm-6 col-xs-12 a">4</div>
          ....
      </div>
  </div>
  ```
  + 可以设置列偏移，让中间保持空隙
  ```python
 <div class="container">
      <div class="row">
          <div class="col-md-8">1-8</div>
          <div class="col-md-3 col-md-offset-1">10-12</div>
      </div>
 </div>
  ```
  + 可以嵌套，嵌满也是 12 列
  ```python
   <div class="container">
       <div class="row">
           <div class="col-md-9">
               <div class="col-md-8">1-8</div>
               <div class="col-md-4">9-12</div>
           </div>
           <div class="col-md-3"> 10-12 </div>
       </div>
   </div>
  ```
  + 可以把两个列交换位置，push 向右移动（推），pull 向左移动（拉）
  ```python
  <div class="container">
      <div class="row">
          <div class="col-md-8 col-md-push-4">8</div>
          <div class="col-md-4 col-md-pull-8">4</div>
      </div>
  </div>
   ```
+ 文本
```python
<p class="text-muted">本行内容是减弱的</p>
<p class="text-primary">本行内容带有一个 primary class</p>
<p class="text-success">本行内容带有一个 success class</p>
<p class="text-info">本行内容带有一个 info class</p>
<p class="text-warning">本行内容带有一个 warning class</p>
<p class="text-danger">本行内容带有一个 danger class</p>
```
+ 背景
```python
<p class="bg-primary">bootstrap课程</p>
<p class="bg-success">bootstrap课程</p>
<p class="bg-info">bootstrap课程</p>
<p class="bg-warning">bootstrap课程</p>
<p class="bg-danger">bootstrap课程</p>
```
+ 关闭按钮 close
```python
<button class="close">×</button>
```
+ 下拉式菜单 caret
```python
<span class="caret"></span>
```
+ 浮动 pull-left pull-right
```python
<div class="pull-left">向左快速浮动</div>
<div class="pull-right">向右快速浮动</div>
```
+ 清除浮动 clearfix
```python
<div class="clearfix" style="background: #D8D8D8;border: 1px solid #000;padding: 10px;">
    <div class="pull-left" style="background:#58D3F7;">向左快速浮动</div>
    <div class="pull-right" style="background: #DA81F5;">向右快速浮动</div>
</div>
```
+ 显示、隐藏 show hide
```python
<div class="row" style="padding: 91px 100px 19px 50px;">
    <div class="show" style="width:300px;background-color:#ccc;"> 这是 show class </div>
    <div class="hidden" style="width:200px;background-color:#ccc;"> 这是 hide class </div>
</div>
```
+ 响应式工具
  + visible-xs visible-sm visible-md visible-lg
  + hidden-xs hidden-sm hidden-md hidden-lg
  + 以超小屏幕（xs）为例，可用的 .visible-*-* 类是：visible-xs-block、visible-xs-inline 和 visible-xs-inline-block
  + visible-print-block visible-print-inline visible-print-inline-block 浏览器隐藏 打印机可见
  ```python
  <div class="container" style="padding: 40px;">
      <div class="row">
          <div class="col-xs-6 col-sm-3" style="background-color: #dedef8;border:1px solid #000;">
              <span class="hidden-xs">特别小型</span>
              <span class="visible-xs">✔ 在特别小型设备上可见</span>
          </div>
          <div class="col-xs-6 col-sm-3" style="background-color: #dedef8;border:1px solid #000;">
              <span class="hidden-sm">小型</span>
              <span class="visible-sm">✔ 在小型设备上可见</span>
          </div>
          <div class="col-xs-6 col-sm-3" style="background-color: #dedef8;border:1px solid #000;">
              <span class="hidden-md">中型</span>
              <span class="visible-md">✔ 在中型设备上可见</span>
          </div>
          <div class="col-xs-6 col-sm-3" style="background-color: #dedef8;border:1px solid #000;">
              <span class="hidden-lg">大型</span>
              <span class="visible-lg">✔ 在大型设备上可见</span>
          </div>
      </div>
  </div>
  ```
+ 下拉菜单
   + 基本的下拉菜单
   ```python
   <div class="dropdown">
       <button class="btn btn-default dropdown-toggle" data-toggle="dropdown">
           Dropdown<span class="caret"></span>
       </button>
       <ul class="dropdown-menu">
           <li><a href="">Html</a></li>
           <li><a href="">Javascript</a></li>
           <li><a href="">jQuery</a></li>
           <li><a href="">html5+css3</a></li>
       </ul>
   </div>
   ```
   + 对齐 dropdown-menu-right
   ```python
      <ul class="dropdown-menu dropdown-menu-right">
           ...
           <li class="dropdown-header">Dropdown header</li>
           ...
      </ul>
   ```
   + 对齐 dropdown-menu-right
   ```python
     <ul class="dropdown-menu">
          ...
          <li class="divider"></li>
          ...
     </ul>
   ```
   + 禁用的菜单项
   ```python
      <ul class="dropdown-menu" aria-labelledby="dropdownMenu4">
          <li><a href="#">Regular link</a></li>
          <li class="disabled"><a href="#">Disabled link</a></li>
          <li><a href="#">Another link</a></li>
      </ul>
   ```
+ 导航（标签）
  + 标签页 nav-tabs
  ```python
   <ul class="nav nav-tabs">
       <li class="active"><a href="">Home</a></li>
       <li><a href="">Project</a></li>
       <li><a href="">Message</a></li>
   </ul>
  ```
  + 胶囊式标签页 nav-pills
    ```python
     <ul class="nav nav-pills">
         <li class="active"><a href="">Home</a></li>
         <li><a href="">Project</a></li>
         <li><a href="">Message</a></li>
     </ul>
    ```
  + 垂直的胶囊式标签页 nav-stacked
    ```python
     <ul class="nav nav-tabs">
         <li class="active"><a href="">Home</a></li>
         <li><a href="">Project</a></li>
         <li><a href="">Message</a></li>
     </ul>
    ```
  + 两端对齐的标签页 nav-justified
    ```python
     <ul class="nav nav-pills nav-justified">
         <li class="active"><a href="">Home</a></li>
         <li><a href="">Project</a></li>
         <li><a href="">Message</a></li>
     </ul>
    ```
  + 禁用链接 disabled
    ```python
     <ul class="nav nav-tabs">
         <li class="active"><a href="">Home</a></li>
         <li class="disabled"><a href="">Project</a></li>
         <li><a href="">Message</a></li>
     </ul>
    ```
  + 带有下拉菜单的标签
    ```python
      <ul class="nav nav-tabs">
          <li class="active"><a href="">Home</a></li>
          <li><a href="">Project</a></li>
          <li class="dropdown">
              <a href="" class="dropdown-toggle" data-toggle="dropdown">Message <span class="caret"></span></a>
              <ul class="dropdown-menu">
                  <li><a href="">关于</a></li>
                  <li><a href="">资讯</a></li>
                  <li><a href="">通讯</a></li>
              </ul>
          </li>
      </ul>
    ```
  + 带下拉菜单的胶囊式标签
    ```python
     <ul class="nav nav-pills">
         <li class="active"><a href="">Home</a></li>
         <li><a href="">Project</a></li>
         <li class="dropdown">
             <a href="" class="dropdown-toggle" data-toggle="dropdown">Message <span class="caret"></span></a>
             <ul class="dropdown-menu">
                 <li><a href="">关于</a></li>
                 <li><a href="">资讯</a></li>
                 <li><a href="">通讯</a></li>
             </ul>
         </li>
     </ul>
    ```
+ 导航条 `navbar <nav>`标签中添加 `class .navbar、.navbar-default`
  + 默认的导航栏
    ```python
       <nav class="navbar navbar-default">
           <div class="navbar-header">
                <a class="navbar-brand" href="">poetries blog</a>
           </div>
           <ul class="nav navbar-nav">
               <li class="active"><a href="">Home</a></li>
               <li><a href="">Project</a></li>
               <li class="dropdown">
                   <a href="" class="dropdown-toggle" data-toggle="dropdown">Message <span class="caret"></span></a>
                   <ul class="dropdown-menu">
                       <li><a href="">关于</a></li>
                       <li><a href="">资讯</a></li>
                       <li><a href="">通讯</a></li>
                   </ul>
               </li>
           </ul>
       </nav>
      ```
      + 响应式的导航栏
      ```python
         <nav class="navbar navbar-default">
             <div class="navbar-header">
                 <button class="navbar-toggle" data-toggle="collapse" data-target="#navbar-collapse">
                     <span class="icon-bar"></span>
                     <span class="icon-bar"></span>
                     <span class="icon-bar"></span>
                 </button>
                 <a class="navbar-brand" href="">教育</a>
             </div>
             <div class="collapse navbar-collapse" id="navbar-collapse">
                 <ul class="nav navbar-nav">
                     <li class="active"><a href="">Home</a></li>
                     <li><a href="">Project</a></li>
                     <li class="dropdown">
                         <a href="" class="dropdown-toggle" data-toggle="dropdown">Message <span class="caret"></span></a>
                         <ul class="dropdown-menu">
                             <li><a href="">关于</a></li>
                             <li><a href="">资讯</a></li>
                             <li><a href="">通讯</a></li>
                         </ul>
                 </li>
                 </ul>
             </div>
         </nav>
      ```
      + 导航栏中的表单`navbar-form`
      ```python
         <form action="" class="navbar-form navbar-right">
             <div class="form-group">
                <input class="form-control" type="text" placeholder="Search"/>
             </div>
             <button class="btn btn-default">Search</button>
         </form>
      ```
      + 导航栏中的按钮 `navbar-btn`
      ```python
           <button class="btn btn-default navbar-btn">Submit</button>
      ```
      + 导航栏中的文本 `navbar-text`
      ```python
           <p class="navbar-text">Signed in as Thomas</p>
      ```
      + 固定到顶部、底部 `navbar-fixed-top navbar-fixed-bottom`
      ```python
           <nav class="navbar navbar-default navbar-fixed-top">
               <div class="navbar-header">
                    <a class="navbar-brand" href="">教育</a>
               </div>
               <ul class="nav navbar-nav">
                   <li class="active"><a href="">Home</a></li>
                   <li><a href="">Project</a></li>
                   <li class="dropdown">
                       <a href="" class="dropdown-toggle" data-toggle="dropdown">Message <span class="caret"></span></a>
                       <ul class="dropdown-menu">
                           <li><a href="">关于</a></li>
                           <li><a href="">资讯</a></li>
                           <li><a href="">通讯</a></li>
                       </ul>
                   </li>
               </ul>
           </nav>
      ```
+ 列表组
  + 向列表组添加国徽
  ```python
        <ul class="list-group">
            <li class="list-group-item"><a href="">免费域名注册 <span class="badge pull-right">20</span></a></li>
            <li class="list-group-item"><a href="">免费 Window 空间托管</a></li>
            <li class="list-group-item"><a href="">每年更新成本</a></li>
        </ul>
  ```
  + 向列表组添加链接
  ```python
      <div class="list-group">
          <a href="" class="list-group-item active">免费域名注册</a>
          <a href="" class="list-group-item">免费 Window 空间托管</a>
          <a href="" class="list-group-item">每年更新成本</a>
      </div>
  ```
  + 向列表组添加自定义内容
  ```python
    <ul class="list-group">
        <li class="list-group-item">Cras justo odio</li>
        <li class="list-group-item">Dapibus ac facilisis in</li>
        <li class="list-group-item">Morbi leo risus</li>
        <li class="list-group-item">Porta ac consectetur ac</li>
        <li class="list-group-item">Vestibulum at eros</li>
    </ul>
  ```
+ 面板
  + 面板标题
  ```python
        <div class="panel-heading">标题</div>
  ```
  + 面板脚注
  ```python
        <div class="panel-footer text-right">by zichen</div>
  ```
  + 面板主题
  ```python
      <div class="panel panel-primary">...</div>
      <div class="panel panel-success">...</div>
      <div class="panel panel-info">...</div>
      <div class="panel panel-warning">...</div>
      <div class="panel panel-danger">...</div>
  ```
  + 带表格的面板
  ```python
    <div class="panel panel-default">
        <div class="panel-heading">Panel heading</div>
        <table class="table">
            <tr>
                <td>学号</td>
                <td>姓名</td>
                <td>年龄</td>
            </tr>
        </table>
    </div>
  ```
  + 带列表组的面板
  ```python
  <div class="panel panel-danger">
      <div class="panel-heading">标题</div>
      <div class="panel-body">面板内容显示区域</div>
      <ul class="list-group">
          <li class="list-group-item">免费域名注册</li>
          <li class="list-group-item">免费 Window 空间托管</li>
          <li class="list-group-item">图像的数量</li>
          <li class="list-group-item">24*7 支持</li>
          <li class="list-group-item">每年更新成本</li>
      </ul>
      <div class="panel-footer text-right">by zichen</div>
  </div>
  ```