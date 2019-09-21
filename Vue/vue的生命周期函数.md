```vue
<div id="app">
	
</div>
<script>
    let vm = new Vue({
        el:"#app",
    }),
    // 这时候$data中没有数据 为undefined
    beforeCreate(){
        console.log('我是beforeCreate生命周期函数');
        debugger;//设置断点
    },
    // 此时已经有$data数据了，但是还不会映射到视图中 数据与根节点没有关联 没有$el   使用ajax请求数据
    created(){
        console.log('我是created生命周期函数');
        debugger;//设置断点
    },
    // 存在$el 数据存在 但是没有挂载到根节点上
    beforeMount(){
        console.log('我是beforeMount生命周期函数');
        debugger;//设置断点
    },
    // 数据已经挂载到视图上了    可以操作节点
    mounted(){
        console.log('我是mounted生命周期函数');
        debugger;//设置断点
    },
    // 在data数据发生改变之前触发
    beforeUpdate(){
        console.log('我是beforeUpdate生命周期函数');
        debugger;//设置断点
    },
    // 在data数据发生改变之后触发
    updated(){
        console.log('我是updated生命周期函数');
        debugger;//设置断点
    },
    // 在实例销毁之前触发
    beforeDestroy(){
        console.log('我是beforeDestroy生命周期函数');
        debugger;//设置断点
    },
    // 在实例销毁之后触发
    destroyed(){
        console.log('我是destroyed生命周期函数');
        debugger;//设置断点
    }
    /*
    vm.$data  获取数据
    vm.$el    获取根节点
    vm.$set(对象，属性，值)
    
    
    vm.$mount(el)
    */
</script>
```

