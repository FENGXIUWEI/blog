---
title: vue项目实战
date: 2018-04-20 10:04:16
bgimage: "/images/vuejs/bg.png"
categories:
- vue.js
tags:
- vue项目实战
---
本篇文章主要介绍了vue的环境配置,vue项目的目录结构以及在开发vue项目中问题的一些解决方案。
### 环境配置及目录结构
1.安装node.js(http://www.runoob.com/nodejs/nodejs-install-setup.html)
2.基于node.js,利用淘宝npm镜像安装相关依赖
  在cmd里直接输入：npm install -g cnpm --registry=https://registry.npm.taobao.org，回车，等待安装...
3.安装全局vue-cli脚手架,用于帮助搭建所需的模板框架
  在cmd里 1)输入：cnpm install -g vue-cli，回车，等待安装...
          2).输入：vue，回车，若出现vue信息说明表示成功
4.创建项目
在cmd里输入：vue init webpack vue_test(项目文件夹名)，回车，等待一小会儿，依次出现‘git’下的项，可按下图操作
![Alt text](/images/vuejs/setting1.png)
5.安装依赖
  在cmd里  1).输入：cd vue_test（项目名），回车，进入到具体项目文件夹
           2).输入：cnpm install，回车，等待一小会儿
  回到项目文件夹，会发现项目结构里，多了一个node_modules文件夹（该文件里的内容就是之前安装的依赖）
  基于脚手架创建的默认项目结构如下图所示：
  ![Alt text](/images/vuejs/setting2.png)
6.测试环境是否搭建成功
  方法1：在cmd里输入：cnpm run dev
  方法2：在浏览里输入：localhost:8080(默认端口为8080)
  运行起来后的效果如下图所示：
  ![Alt text](/images/vuejs/setting3.png)

项目的目录结构：
  assets：主要放置样式文件和图片
  components：组件
  lib：放置模拟好的数据
  router：放置路由信息
  store：放置vuex的文件
  views：放置所有的单页面
### 使用Vuex步骤
1.使用npm安装：
  npm install vuex --save
2.引入vuex插件
创建文件夹store，新建index.js，import Vue和Vuex，Vue的插件引入函数Vue.use()使用Vuex,Vue.use(Vuex)
store/index.js
```
import Vue from 'vue'
import Vuex from 'vuex'
Vue.use(Vuex)
let store = new Vuex.Store({})
```
main.js中引入store，在Vue实例中注册store对象
```
import Vue from 'vue'
import App from './App'
import router from './router'

import store from './store'
Vue.config.productionTip = false
new Vue({
  el: '#app',
  router,
  store,
  template: '<App/>',
  components: { App }
})
```
3.将状态映射到组件
store/index.js
```
import Vue from 'vue'
import Vuex from 'vuex'
Vue.use(Vuex)
let store = new Vuex.Store({
  state: {
    receiveInfo: [{
      'name': '王某某',
      'phone': '13811111111',
      'areaCode': '010',
      'landLine': '64627856',
      'provinceId': 110000,
      'province': '北京市',
      'cityId': 110100,
      'city': '市辖区',
      'countyId': 110106,
      'county': '海淀区',
      'add': '上地十街辉煌国际西6号楼319室',
      'default': true,
      'checked': true
    }, {
      'name': '李某某',
      'phone': '13811111111',
      'areaCode': '010',
      'landLine': '64627856',
      'provinceId': 110000,
      'province': '北京市',
      'cityId': 110100,
      'city': '市辖区',
      'countyId': 110106,
      'county': '海淀区',
      'add': '上地十街辉煌国际东6号楼350室',
      'default': false,
      'checked': false
    }]
  }
})
```
组件中修改状态
```
export default {
  computed: {
    receiveInfo: function () {
      return this.$store.state.receiveInfo
    }
  }
}
```
getters:过滤state数据
mutations:显式的更改state里的数据
### vue中关于props和$emit的用法
1.父组件可以使用props把数据传给子组件
props是父组件用来传递数据的一个自定义属性。父组件的数据需要通过props把数据传递给子组件，子组件需要显示地用props选项声明props
父组件
```
<address-pop v-if="popShow" @close="closePop" :oldReceive="oldReceive"></address-pop>
```
子组件
```
props: {
  oldReceive: {
    type: Object
  },
  receiveIndex: {
    type: Number
  }
}
```
2.子组件可以使用$emit触发父组件的自定义事件
父组件定义了一个close事件，在子组件中直接通过this.$emit('close')调用父组件中的close方法
父组件
```
<address-pop v-if="popShow" @close="closePop" :oldReceive="oldReceive"></address-pop>
<script>
import addressPop from '@/components/address-pop'
export default {
components: {
  addressPop
},
methods: {
  closePop: function () {
    this.popShow = false
  }
}
}
```
子组件
```
<span class="dialog-close" @click="closePop">x</span>
export default {
methods: {
  closePop: function () {
  this.$emit('close')
}
}
```
