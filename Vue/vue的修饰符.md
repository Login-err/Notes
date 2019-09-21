```vue
/*
	this.$refs  获取所有含有ref标记的节点


*/
```



```html
<!--
    .once  只执行一次   使用方式  @click.once = "fn"
	.stop  阻止事件冒泡
	.self  只有在自身元素上触发事件
	.prevent  阻止元素的默认行为
	.captrue 为事件绑定一个捕获阶段触发的函数
	前四个比较常用
-->
<div id="app">
    <div @click.once="fn">
        
    </div>
</div>
<script>
    const vm = new Vue({
        el:"#app",
        data:{},
        methons:{
            fn(){}
        }
    })
</script>
```

