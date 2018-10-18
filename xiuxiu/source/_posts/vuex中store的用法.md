---
title: vuex中store的用法
date: 2018-04-20 10:04:16
bgimage: "/images/vuejs/bg.png"
categories:
- vue.js
tags:
- vuex中store的用法
---
本篇文章主要介绍了Vuex之理解Store的用法，Store类就是存储数据和管理数据方法的仓库，实现方式是将数据和方法已对象形式传入其实例中
### [](#1.什么是Store？ "1.什么是Store？")1.什么是Store？
Vuex就是提供一个仓库，Store仓库里面放了很多对象。其中state就是数据源存放地，对应于与一般Vue对象里面的data（后面讲到的actions和mutations对应于methods）。
在使用Vuex的时候通常会创建Store实例new Vuex.store({state,getters,mutations,actions})有很多子模块的时候还会使用到modules
![Alt text](/images/vuex/1.png)
Store类就是存储数据和管理数据方法的仓库，实现方式是将数据和方法已对象形式传入其实例中。要注意一个应用或是项目中只能存在一个Store实例！！
### [](#3.store.js的核心 "3.store.js的核心")3.store.js的核心
状态管理有5个核心，分别是state、getter、mutation、action以及module。分别简单的介绍一下它们：
#### 1) state
state为单一状态树，在state中需要定义我们所需要管理的数组、对象、字符串等等，只有在这里定义了，在vue.js的组件中才能获取你定义的这个对象的状态。
#### 2) getter
getter有点类似vue.js的计算属性，当我们需要从store的state中派生出一些状态，那么我们就需要使用getter，getter会接收state作为第一个参数，而且getter的返回值会根据它的依赖被缓存起来，只有getter中的依赖值（state中的某个需要派生状态的值）发生改变的时候才会被重新计算。
#### 3) mutation
更改store中state状态的唯一方法就是提交mutation，就很类似事件。每个mutation都有一个字符串类型的事件类型和一个回调函数，我们需要改变state的值就要在回调函数中改变。我们要执行这个回调函数，那么我们需要执行一个相应的调用方法：store.commit。
#### 4) action
 action可以提交mutation，在action中可以执行store.commit，而且action中可以有任何的异步操作。在页面中如果我们要使用这个action，则需要执行store.dispatch
#### 5) module
module其实只是解决了当state中很复杂臃肿的时候，module可以将store分割成模块，每个模块中拥有自己的state、mutation、action和getter。
### [](#2.store.js的写法 "2.store.js的写法")2.store.js的写法
````
import Vue from 'vue'
import Vuex from 'vuex'
Vue.use(Vuex)

let store = new Vuex.Store({
  state: {
    carPanelData: [],
    maxOff: false,
    // 是否为最大值,为最大值的时候弹出对话框
    carShow: false,
    // 购物车是否隐藏
    carTimer: null,
    // 创建一个小球，记录相关的信息
    ball: {
      show: false,
      // 哪一个按钮
      el: null,
      // 图片地址
      img: ''
    }
  },
  getters: {
    totalCount: function (state) {
      let count = 0
      state.carPanelData.forEach((goods) => {
        count += goods.count
      })
      return count
    },
    totalPrice: function (state) {
      let price = 0
      state.carPanelData.forEach((goods) => {
        price += goods.count * goods.price
      })
      return price
    }
  },
  // 建立一个方法
  mutations: {
    addCarPanelData: function (state, data) {
      let boff = true
      state.carPanelData.forEach((goods) => {
        if (goods.sku_id === data.sku_id) {
          goods.count++
          boff = false
          if (goods.count > goods.limit_num) {
            goods.count--
            state.maxOff = true
            return false
          }
          /* state.ball.el = event.path[0] */
          /* state.ball.show = true
          state.ball.img = data[0].ali_image
          boff = false */
          console.log(event)
          // 加成功后显示弹出框
          state.carShow = true
        }
      })
      if (boff) {
        let goodsData = data
        Vue.set(goodsData, 'count', 1)
        state.carPanelData.push(goodsData)
        // 加成功后显示弹出框
        state.carShow = true
        // event 存在浏览器的兼容性问题
        /* state.ball.el = event.path[0] */
        /* state.ball.show = true
        state.ball.img = data[0].ali_image
        boff = false */
        console.log(event)
      }
    },
    deleteCarPanelData: function (state, id) {
      state.carPanelData.forEach((goods, index) => {
        if (goods.sku_id === id) {
          state.carPanelData.splice(index, 1)
          return false
        }
      })
    },
    closePrompt: function (state) {
      state.maxOff = false
    },
    alertPrompt: function (state) {
      state.maxOff = true
    },
    showCar: function (state) {
      clearTimeout(state.carTimer)
      state.carShow = true
    },
    hideCar: function (state) {
      state.carTimer = setTimeout(() => {
        state.carShow = false
      }, 500)
    }
  }
})

export default store
````