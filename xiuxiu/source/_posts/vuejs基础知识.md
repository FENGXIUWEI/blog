---
title: vuejs基础知识
date: 2018-10-31 15:48:35
tags:
- vue.js
categories:
- vue.js
---
vue.js官网地址：https://cn.vuejs.org/

##### 基本配置总结
1.手机上访问项目
在package.json页面中的scripts对象中dev字段中添加--host 0.0.0.0
![vue.js基础知识](/images/vuejs/base/vue_host.png)
2.静态文件和数据的存放
static目录下的文件并不会被 Webpack 处理：它们会直接被复制到最终目录（默认是`dist/static`）下
为了方便路径的填写可以webpack.base.config.js文件中给此文件设置一个别名
![vue.js基础知识](/images/vuejs/base/vue_static.png)
对于此文件存放的静态数据，为了方便接口联调可以在config文件夹下的index.js中设置代理配置表的信息
![vue.js基础知识](/images/vuejs/base/vue_config_index.png)
#### vue.js的基础使用
1.vue组件的基本组成
```python
<template>
    <div></div>
</template>
<script>
    export default {
        name: "home"
    }
</script>
<style lang="stylus" scope>
</style>
```
2.vue组件中name的作用
  + 当项目使用keep-alive时，可搭配组件name进行缓存过滤
  因为我们在App.vue中使用了keep-alive导致我们第二次进入的时候页面不会重新请求，即触发mounted函数。
  解决方案：
    1）增加activated()函数,每次进入新页面的时候再获取一次数据
    2）在keep-alive中增加一个过滤
  ```python
    <div id="app">
      <keep-alive exclude="Detail">
        <router-view/>
      </keep-alive>
    </div>
   ```
  + DOM做递归组件时
  ```python
  <template>
    <div >
      <div class="item" v-for="(item,index) of categoryList" :key="index">
        <div class="item-title border-bottom">
          <span class="item-title-icon"></span>
          {{item.title}}
        </div>
        <div v-if="item.children" class="item-chilren">
          <detail-list :categoryList="item.children"></detail-list>
        </div>
      </div>
    </div>
  </template>

  <script>
  export default {
    name: 'DetailList',
    props: {
      categoryList: Array
    }
  }
  ```
  </script>
  + 当你用vue-tools时
  vue-devtools调试工具里显示的组见名称是由vue中组件name决定的
  ![vue.js基础知识](/images/vuejs/base/vue_dev_tool.png)

3.vue.js 生命周期函数
  + beforeCreate（创建前）
  + created（创建后）
  + beforeMount（载入前）
  + mounted（载入后）
  + beforeUpdate（更新前）
  + updated（更新后）
  + beforeDestroy（销毁前）
  + destroyed（销毁后）
  ```python
  <html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>vue生命周期学习</title>
    <script src="https://cdn.bootcss.com/vue/2.4.2/vue.js"></script>
  </head>
  <body>
  <div id="app">
    <input v-model="message" />
    <h1>{{message1}}</h1>
  </div>
  <script>
  var vm = new Vue({
    /*创建vue对象*/
    el: '#app',
    /****挂载目标****/
    data: {
      /****数据对象****/
      message: 'Hello World!'
    },
    computed: {
      /****实现某一属性的实时计算****/
      message1: function () {
        return this.message.split("").reverse().join("");
      }
    },
    watched: {
      /****检测某一属性值的变化****/
    },
    methods: {
      /****组件内部的方法****/
    },
    beforeCreate: function () {
      console.group('------beforeCreate创建前状态------');
      console.log("%c%s", "color:red", "el     : " + this.$el); //undefined
      console.log("%c%s", "color:red", "data   : " + this.$data); //undefined
      console.log("%c%s", "color:red", "message: " + this.message)//undefined
    },
    //1.在beforeCreate和created钩子之间，程序开始监控Data对象数据的变化及vue内部的初始化事件
    created: function () {
      console.group('------created创建完毕状态------');
      console.log("%c%s", "color:red", "el     : " + this.$el); //undefined
      console.log("%c%s", "color:red", "data   : " + this.$data); //已被初始化
      console.log("%c%s", "color:red", "message: " + this.message); //已被初始化
    },
    // 2.在created和beforeMount之间，判断是否有el选项，若有则继续编译，无，则暂停生命周期；
    //然后程序会判断是否有templete参数选项，若有，则将其作为模板编译成render函数。若无，则将外部html作为模板编译（template优先级比外部html高）
    beforeMount: function () {
      console.group('------beforeMount挂载前状态------');
      console.log("%c%s", "color:red", "el     : " + (this.$el)); //已被初始化 console.log(this.$el);
      console.log("%c%s", "color:red", "data   : " + this.$data); //已被初始化
      console.log("%c%s", "color:red", "message: " + this.message); //已被初始化
    },
    // 3.在beforeMount和mounted之间，程序将上一步编辑好的html内容替换el属性指向的dom对象或者选择权对应的html标签里面的内容
    mounted: function () {
      console.group('------mounted 挂载结束状态------');
      console.log("%c%s", "color:red", "el     : " + this.$el); //已被初始化
      console.log(this.$el);
      console.log("%c%s", "color:red", "data   : " + this.$data); //已被初始化
      console.log("%c%s", "color:red", "message: " + this.message); //已被初始化
    },
    // 4.mounted和beforeUpdate之间，程序实时监控数据变化
    beforeUpdate: function () {
      console.group('beforeUpdate 更新前状态===============》');
      console.log("%c%s", "color:red", "el     : " + this.$el);
      console.log(this.$el);
      console.log("%c%s", "color:red", "data   : " + this.$data);
      console.log("%c%s", "color:red", "message: " + this.message);
    },
    // 5.beforeUpdate和updated之间，实时更新dom
    updated: function () {
      console.group('updated 更新完成状态===============》');
      console.log("%c%s", "color:red", "el     : " + this.$el);
      console.log(this.$el);
      console.log("%c%s", "color:red", "data   : " + this.$data);
      console.log("%c%s", "color:red", "message: " + this.message);
    },
    beforeDestroy: function () {
      console.group('beforeDestroy 销毁前状态===============》');
      console.log("%c%s", "color:red", "el     : " + this.$el);
      console.log(this.$el);
      console.log("%c%s", "color:red", "data   : " + this.$data);
      console.log("%c%s", "color:red", "message: " + this.message);
    },
    //6.实例销毁
    destroyed: function () {
      console.group('destroyed 销毁完成状态===============》');
      console.log("%c%s", "color:red", "el     : " + this.$el);
      console.log(this.$el);
      console.log("%c%s", "color:red", "data   : " + this.$data);
      console.log("%c%s", "color:red", "message: " + this.message)
    }
  })
  </script>
  </body>
  </html>
  ```
4.MVVM和MVP设计模式
  + MVVM框架（面向数据开发）
    Model：代表你的基本业务逻辑
    View：显示内容
    ViewModel：将前面两者联系在一起的对象，是vue自带的，可以监测到数据的变化，没有任何Dom操作
  + MVP框架（面向Dom开发）
    Model：通过Ajax调用数据
    View：视图，页面的html代码
    Presenter：可以理解为控制层点击的时候控制器通过dom操作改变试图







