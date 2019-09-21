##### vuex

```javascript
/*
* 使用先按照 npm install vuex --save
* 在src里面新建一个store文件夹，在store文件夹里面新建一个index.js
* ./store/index.js里面
*/
import Vue from 'vue';
import Vuex from 'vuex'
import Axios from 'axios'
Vue.use(Vuex)
export default new Vuex.Store({
    state:{
        userLogin:'',
        userList;[]
    },
    // 放置同步的修改state数据的方法，第一个参数默认为state，第二个参数可传可不传，this.$store.commit('saveLoginUser',第二个参数的值)
    mutation:{
        saveLoginUser(state,value){
            state.userLogin = value
        },
        saveUserlist(state,value){
            state.userList = value
        }
    },
    // 放置异步的修改state数据的方法，里面的cxt具有store的所有属性和方法，但是两者不相等
	actions:{
        getUserList(cxt){
            this.$axios.get('url').then((data)=>{
                cxt.commit('saveUserlist',value)
            })
        }
    },
    //getters里面的默认传递的第一个参数为state  
    getters:{
        abc:(state)=>{}
    }
})
```

##### 添加$store属性

```javascript
//main.js
import store from './store/index'
new Vue({
    el:"#app",
    router,
    store,
  	components: { App },
  	template: '<App/>'
})
```



###### 其他地方将东西注入仓库

```javascript
//辅助函数
import {mapState,mapActions} from 'vuex'
computed:{
    ...mapState(['属性名'])
}
methods:{
    ...mapActions(['函数名'])
}
this.$store.commit('saveLoginUser',value);//此处的saveLoginUser应该与store里面的mutation里面的方法一致
this.$store.dispatch('getUserList')
```

