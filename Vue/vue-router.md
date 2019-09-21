###### router-link一般与router-view配套使用，router-view为router-link的出口，但是router-view在匹配到路由的时候，就会渲染该路由所对应的组件

###### 如果在一个模块化工程中使用它，必须要通过 `Vue.use()` 明确地安装路由功能

```javascript
// npm install vue-router  npm安装

import Vue from 'vue'
import VueRouter form 'vue-router'
Vue.use(VueRouter)
```

```javascript
import A from '@/component/A'
import B from '@/component/B'
import C from '@/component/C'
//路由映射表
const routes = [
    {path:'/a',name:'alink',component:A}
    {path:'/b',name:'blink',component:B}
    {path:'/c',name:'clink',component:C}
]
//创建router实例
const router = new VueRouter({
    routes
})
//创建和挂载根实例
const app = new Vue({
    el:"#app",
    router
})
//我们现在可以在任何组件内通过 this.$router 访问路由器，也可以通过 this.$route 访问当前路由：
```

```javascript
import router from 'vue-router'
//如果导入router的话
//this.$router与router使用起来完全一样
```

##### 动态路由

```javascript
const routes = [
    //动态路由参数 以冒号开头
    {path:'/a/:id',name:'alink',component:A}
    {path:'/b',name:'blink',component:B}
    {path:'/c',name:'clink',component:C}
]
```

| **模式**                      |    **匹配路径**     |          **$route.params**           |
| ----------------------------- | :-----------------: | :----------------------------------: |
| /user/:username               |     /user/evan      |         { username: 'evan' }         |
| /user/:username/post/:post_id | /user/evan/post/123 | { username: 'evan', post_id: '123' } |

##### 嵌套路由

```javascript
 routes: [
    { path: '/user/:id', component: User,
      children: [
        {
          // 当 /user/:id/profile 匹配成功，
          // UserProfile 会被渲染在 User 的 <router-view> 中
          //此处的path选项里面不需要加/
          path: 'profile',
          component: UserProfile
        },
        {
          // 当 /user/:id/posts 匹配成功
          // UserPosts 会被渲染在 User 的 <router-view> 中
          path: 'posts',
          component: UserPosts
        }
      ]
    }
  ]
```

#####  编程式的导航

###### 除了使用 `<router-link>` 创建 a 标签来定义导航链接，我们还可以借助 router 的实例方法，通过编写代码来实现。

###### ```router.push(location, onComplete?, onAbort?)```**在 Vue 实例内部，你可以通过 $router 访问路由实例。因此你可以调用 this.$router.push**

```javascript
// 字符串
router.push('home')

// 对象
router.push({ path: 'home' })

// 命名的路由
router.push({ name: 'user', params: { userId: '123' }})

// 带查询参数，变成 /register?plan=private
router.push({ path: 'register', query: { plan: 'private' }})
```

