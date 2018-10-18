---
title: Vue.js的基本使用
date: 2018-04-20 17:11:46
bgimage: "/images/vuejs/bg.png"
tags:
- vue.js
categories:
- Vue.js的基本使用
---
#### 路由的使用

1. 安装路由模块

```
Npm install vue-router --save
```

2. 引入模块

```
import VueRouter from ‘vue-router’
```

3. 作为vue的插件

```
Vue.use(VueRouter)
```

4. 创建路由实例对象

```
New VueRouter({
...配置参数
})
```

5. 注入vue选项参数

```
New Vue({
router
})
```

6. 告诉路由渲染的位置

```
<router-view></router-view>
```
#### Hash 和 History 模式

vue-router默认 hash 模式 "#" url的hash模式，mode:history模式就是正常的路径模式,history带来的便利是可以使用浏览器的前进后退功能

```
export default new Router({
  mode: 'history',
  routes: [
    {
      path: '/home',
      name: 'Home',
      component: Home
    },
    {
      path: '/project',
      name: 'Project',
      component: Project
    },
    {
      path: '/doc',
      name: 'Document',
      component: Document
    }

  ]
})
```

####  router-link的各项配置

router-link 组件支持用户在具有路由功能的应用中（点击）导航。 通过 to 属性指定目标地址，默认渲染成带有正确链接的 a 标签，可以通过配置 tag 属性生成别的标签.。另外，当目标路由成功激活时，链接元素自动设置一个表示激活的 CSS 类名

```
<router-link :to="{path:'/project'}" active-class="activeClass" tag='li' event='mouseover'>
  <i class="fa fa-home"></i>
  <span>project</span>
</router-link>
```
to：目标路由的链接，此链接可以进行动态绑定的，tag：渲染成某种标签，如:li,event:默认为点击事件，也可以将其设置为鼠标移入的事件，mouseover

```
<router-link :to='index' tag='li' event='mouseover'>
  <i class="fa fa-home"></i>
  <span>Home</span>
</router-link>


<script>
export default {
  name: 'App',
  data () {
    return {
      index: '/home'
    }
  }
}
</script>
```

active-class：设置 链接激活时使用的 CSS 类名。默认值可以通过路由的构造选项 linkActiveClass 来全局配置

```
//路由中设置

export default new Router({
  mode: 'history',
  linkActiveClass: 'is-active',
  routes: [
    {
      path: '/home',
      name: 'Home',
      component: Home,
      // 路由中的别名
      alias: '/index'
    },
    {
      path: '/project',
      name: 'Project',
      component: Project
    },
    {
      path: '/doc',
      name: 'Document',
      component: Document
    }

  ]
})

//组件中进行设置

<router-link :to="{path:'/project'}" active-class="activeClass" tag='li' event='mouseover'>
    <i class="fa fa-home"></i>
    <span>project</span>
</router-link>
```

####  重定向和别名

```
export default new Router({
  mode: 'history',
  linkActiveClass: 'is-active',
  routes: [
    {
      path: '/home',
      name: 'Home',
      component: Home,
      // 路由中的别名
      alias: '/index'
    },
    {
      path: '/project',
      name: 'Project',
      component: Project
    },
    {
      path: '/doc',
      name: 'Document',
      component: Document
    },
    // 如果没有以上的地址，就将跳转到home页面
    {
      path: '*',
      // component: Home
      // redirect: '/home'
      // redirect:{path: '/home'}
      // redirect:{name: 'Home'}
      // 动态设置重定向的目标路径
      redirect: (to) => {
        // 目标路由对象，就是访问的路径的路由信息
        if (to.path === '/123') {
          return '/home'
        } else if (to.path === '/456') {
          return {path: '/doc'}
        } else {
          return {name: 'Project'}
        }
        // return '/home'
      }
    }

  ]
})
```

####  嵌套路由使用

exact："是否激活" 默认类名的依据是 inclusive match （全包含匹配）

```
<router-link to='/' exact tag='li' event='mouseover'>
    <i class="fa fa-home"></i>
    <span>Home</span>
</router-link>
```

子路由的配置

```
export default new Router({
  mode: 'history',
  linkActiveClass: 'is-active',
  routes: [
    {
      path: '/',
      component: Home
    },
    {
      path: '/home',
      name: 'Home',
      component: Home,
      alias: '/index'
    },
    {
      path: '/project',
      component: Project,
      children: [
        {
          path: '',
          name: 'Project',
          // 默认子路由，有默认子路由就不要再父路由中设置name属性
          component: study
        },
        {
          path: 'work',
          name: 'work',
          component: work
        },
        {
          path: 'hobby',
          name: 'hobby',
          component: hobby
        }
      ]
    },
    {
      path: '/doc',
      name: 'Document',
      component: Document
    }
  ]
})
```

#### 命名视图

子路径的格式为：http://localhost:8081/work，即在子路径中加了/，就相对于跟路径来说的，子路径不需要嵌套，但是组件需要嵌套的。。

```
//vue页面的写法，动态的绑定路径

<ul class="nav">
    <router-link :to="{name: 'Project'}" exact tag='li'>
    <a>study</a>
    </router-link>

    <router-link :to="{name: 'work'}" tag='li'>
    <a>work</a>
    </router-link>

    <router-link :to="{name: 'hobby'}" tag='li'>
    <a>hobby</a>
    </router-link>
</ul>

//路由的配置

export default new Router({
  mode: 'history',
  linkActiveClass: 'is-active',
  routes: [
    {
      path: '/',
      component: Home
    },
    {
      path: '/home',
      name: 'Home',
      component: Home,
      alias: '/index'
    },
    {
      path: '/project',
      component: Project,
      children: [
        {
          path: '',
          name: 'Project',
          component: study
        },
        {
          path: '/work',
          name: 'work',
          component: work
        },
        {
          path: '/hobby',
          name: 'hobby',
          component: hobby
        }
      ]
    },
    {
      path: '/doc',
      name: 'Document',
      component: Document
    }
  ]
})
```
多个router-view的应用

```
//app.vue

<router-view name="slider"></router-view>
<router-view class="center"></router-view>

//路由中的配置，一个路径对应一个组件用component，一个路径对应多个组件，用Components，默认的组件用default，其他的组件用router-view中name的值

export default new Router({
  mode: 'history',
  linkActiveClass: 'is-active',
  routes: [
    {
      path: '/',
      component: Home
    },
    {
      path: '/home',
      name: 'Home',
      component: Home,
      alias: '/index'
    },
    {
      path: '/project',
      component: Project,
      children: [
        {
          path: '',
          name: 'Project',
          component: study
        },
        {
          path: '/work',
          name: 'work',
          component: work
        },
        {
          path: '/hobby',
          name: 'hobby',
          component: hobby
        }
      ]
    },
    {
      path: '/doc',
      name: 'Document',
      components: {
        default: Document,
        slider: slider
      }
    }
  ]
})
```

#### 动态路径

匹配到的所有路由，全都映射到同一个组件
路径:/user/:userId,userId为动态路径参数

获取参数：路由信息对象的params

#### 监控 $route 路由信息对象

$router router 实例对象
$route 当前激活的路由信息对象，每个组件实例都会有
路由信息对象（一个路由信息对象表示当前激活的路由的状态信息，每次成功的导航后都会产生一个新的对象）

````
<script>
let data = [
  {
    id: 1,
    tip: 'vip',
    userName: 'leo1',
    sex: '男',
    hobby: '写代码'
  },
  {
    id: 2,
    tip: 'vip',
    userName: 'leo2',
    sex: '男',
    hobby: '唱歌'
  },
  {
    id: 3,
    tip: 'common',
    userName: 'leo3',
    sex: '男',
    hobby: '读书'
  }
]
export default{
  data () {
    return {
      userList: data,
      userInfo: {}
    }
  },
  // 如何知道路由对象发生了变化,通过watch的方法监控route的变化
  watch: {
    $route () {
      // 路径发生变化，$route会重新赋值，监控这个属性，会执行这个函数
      this.getData()
    }
  },
  // 生命周期，编译之前,刚生成的时候执行created，后来不会重新生成，就不会执行钩子函数
  created () {
    // 渲染这个组件会调用一次这个生命周期函数
    // 复用这个组件，这个函数不会再次被调用的
    // 地址一旦发生变化，$route 会重新生成一个路由信息对象
    this.getData()
  },
  // 将公共的方法放入到methods函数中
  methods: {
    getData () {
      let id = this.$route.params.userId
      if (id) {
        this.userInfo = this.userList.filter((item) => {
          return parseInt(item.id) === parseInt(id)
        })[0]
      } else {
        this.userInfo = {}
      }
    }
  }
}
</script>
````

beforeRouterEnter() 进入组件的勾子函数

#### Query 字符串传参

````
<div class="info-list" style="font-size:20px;" v-if="userInfo.userName">
  <router-link exact :to="{path:'',query:{info:'follow'}}">我的关注</router-link>
  <router-link exact :to="{path:'',query:{info:'share'}}">我的分享</router-link>
  <div >
  {{$route.query}}
  </div>
</div>
````

#### 过渡动效
提供了transition的封装组件，添加过渡动画，添加删除css类名
v-enter:定义进入过渡的开始状态
v-enter-active:定义进入活动状态
v-enter-to:定义进入的结束状态
v-leave:定义李凯过渡的开始状态
v-leave-active:定义离开活动状态
v-leave-to:定义离开的结束状态

过渡模式：

in-out：新元素先进行过去，完成之后当前元素过渡离开
out-in:当前元素进行过渡，完成之后新元素过渡进入

````
<transition mode="out-in">
  <router-view class="center"></router-view>
</transition>
<style>
.v-enter{
opacity:0;
}
.v-enter-to{
opacity:1;
}
.v-enter-active{
transition:1s;
}
.v-leave{
opacity:1;
}
.v-leave-to{
opacity:0;
}
.v-leave-active{
transition:2s;
}
</style>
````

#### 动态设置name属性左右切换

自定义设置transition的效果

````
 <transition  name="left">
      <router-view class="center"></router-view>
 </transition>
 <style>
 .left-enter{
 transform:translateX(100%)
 }
 .left-enter-to{
 transform:translateX(0)
 }
 .left-enter-active{
 transition:1s;
 }
 .left-leave{
 transform:translateX(0)
 }
 .left-leave-to{
 transform:translateX(-100%)
 }
 .left-leave-active{
 transition:1s;
 }
 </style>
````
动态设置name属性左右切换
```
// vue页面的设置

<transition :name="names">
      <router-view class="center"></router-view>
</transition>

// js中的设置

export default {
  name: 'App',
  data () {
    return {
      index: '/home',
      names: 'names'
    }
  },
  watch: {
    $route (to, from) {
      if (to.meta.index < from.meta.index) {
        console.info(to.meta.index + '===')
        this.names = 'right'
      } else {
        console.info(to.meta.index + '===')
        this.names = 'left'
      }
    }
  }
  }

 // router文件夹下面的 index.js 的设置

routes: [
    {
      path: '/',
      component: Home,
      meta: {
        index: 0
      }
    },
    {
      path: '/home',
      name: 'Home',
      component: Home,
      alias: '/index',
      meta: {
        index: 0
      }
    },
    {
      path: '/project',
      component: Project,
      children: [
        {
          path: '',
          name: 'Project',
          component: study,
          meta: {
            index: 1
          }
        },
        {
          path: '/work',
          name: 'work',
          component: work
        },
        {
          path: '/hobby',
          name: 'hobby',
          component: hobby
        }
      ]
    },
    {
      path: '/doc',
      name: 'Document',
      components: {
        default: Document,
        slider: slider
      },
      meta: {
        index: 2
      }
    },
    {
      path: '/user/:tip?/:userId?',
      name: 'user',
      component: user,
      meta: {
        index: 3
      }
    }
    }
    ]
    ```

#### 编程式导航
借助于router的实例方法，通过编写代码来实现导航的切换
back 回退一步
forward 前进一步
go 指定前进后退步数
push 导航到不同url，向history栈添加一个新的记录
replace 导航到不同url，替换history栈中当前记录

 ```
// vue 页面的写法

<input type="button" value="后退" @click="backHandle" />
<input type="button" value="前进" @click="forwardHandle" />
<input type="button" value="控制前进后退的步数" @click="goHandle" />
<input type="button" value="控制导航的指定push" @click="pushHandle" />
<input type="button" value="控制导航的指定replace" @click="replaceHandle" />

// js 页面的写法

 methods: {
    backHandle () {
      console.info('后退')
      this.$router.back()
    },
    forwardHandle () {
      console.info('前进')
      this.$router.forward()
    },
    goHandle () {
      // 前进 为正数，后退为负数
      this.$router.go(2)
    },
    pushHandle () {
      // 前进 为正数，后退为负数
      this.$router.push({path: '/doc'})
    },
    replaceHandle () {
      // 前进 为正数，后退为负数
      this.$router.replace({path: '/doc'})
    }
  }

 ```

 #### 导航钩子函数
 导航发生变化时，导航钩子主要用来拦截导航，让它完成跳转或取消
 执行钩子函数位置
 router全局
 单个路由
 组件中
 钩子函数
 router实例上：beforsEach，afterEach
 单个路由中：beforeEnter
 组件内的钩子：beforeRouterEnter，beforeRouterUpdate，beforeRouterLeave
 钩子函数接收的参数
 to：要进入的目标路由对象，到哪里去
 from：正要离开导航的路由对象，从哪儿来
 next：用来决定跳转或取消导航
 ```
// 切换不同的导航，钩子函数都会被执行
router.beforeEach((to, from, next) => {
console.log('beforeEach')
// 想要进入导航必须要执行以下next(),next(false)
if(to.meta.login) {
 next('/login')
} else {
 next()
}
})
// 移入不同导航时，需要修改页面的title值
router.afterEach((to, from) => {
if(to.meta.title) {
 window.document.title = to.meta.title
} else {
 window.document.title = 'peixiu'
}
})
```

单个路由设置

```
routes: [
 {
   path: '/',
   component: Home,
   beforeEnter (to, from, next) {
     if (to.meta.login) {
       next('/login')
     } else {
       next()
     }
   }
}
]
```




