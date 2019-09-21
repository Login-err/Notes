##### vue.extend

```html
<!--Vue.extend 就是用来生成组件，学vue就是不停的使用组件-->
<!--标签模板-->
<abc></abc>
<div id="box"></div>
<script>
    let extend = Vue.extend({
        template:`<h2><a :href="url">{{con}}</a></h2>`,
        data(){
            return{
                con:'extend',
                url:'http://baidu.com'
            }
        }
    });
    new extend().$mount('abc');//挂载
    new extend().$mount('#box');
</script>
<!--效果地址（http://localhost:63342/htdocs/Feweb/%E6%BD%AD%E5%B7%9E%E4%BD%9C%E4%B8%9A/%E8%BF%BD%E6%A2%A6%E8%80%81%E5%B8%88/Vue/%E5%85%A8%E5%B1%80API/vue.extend.html?_ijt=q2gkjr2u2l9jdqpct8r55puiqb）-->
```

##### vue.nextTick

###### 在下次DOM更新循环结束之后执行延时回调。在修改数据之后立即使用这个方法，获取更新后的DOM

```html
<div id="app">{{msg}}</div>
<script>
    let app = new Vue({
        el:'#app',
        data(){
            return {
                msg:'hello'
            }
        }
    })
    app.msg = '你好';
    Vue.nextTick(function(){
        console.log('DOM更新了')
    })
    Vue.nextTick().then(()=>{
        console.log('DOM更新了')
    })
</script>
```

##### Vue.set

```html
<div id="app"></div>
<script>
    let app = new Vue({
        el:'#app',
        data(){
            return {
                arr:['a','b','c'];
            }
        }
    })
    Vue.set(app.arr,2,'123');//三个参数分别代表 目标（要修改的地方）  索引值   要修改的值
</script>
```

##### Vue.delect

```html
<div id="app"></div>
<script>
    let app = new Vue({
        el:'#app',
        data(){
            return {
                arr:['a','b','c'];
            }
        }
    })
    Vue.delect(app.arr,2);//三个参数分别代表 目标（要删除的地方）  删除的位置
</script>
```

##### Vue.directive

```html
<!--
	Vue.directive 自定义指令
-->
<div id="app">
    <h1>{{msg}}</h1>
    <h2 v-dream="custom">{{msg}}</h2>
    <h2 v-coutom="info">{{msg}}</h2>
</div>
<script>
    function unbind(){
        app.$destory();
    }
    Vue.directive('dream',function(el,bind){
        console.log( el );//该标签<h2 v-dream="custom">{{msg}}</h2>
        el.style = 'color:' + bind.value;
        console.log(bind);//一个对象
    });
    Vue.directive('coutom',{
        bind:function(){
            console.log('1. 被绑定');
        },
        inserted: function(){
        	console.log('2. 绑定到节点');
    	},
        updata: function(){
            console.log('3. 组件更新');
        },
        componentUpdated: function(){
            console.log('4. 组件更新完成');
        },
        unbind: function(){
            console.log('5. 解绑');
        }
    })
    new Vue({
        el:'#app',
        data:{
            msg:'Vue.directive',
            custom:'hotpink',
            info:'blue',
            num:0
        },
        methods:{
            add(){
                this.num++;
            }
        }
    })
</script>
```

##### Vue.filter

```html
<div>
    <h1>{{msg}}</h1>
	<h2>{{text | myFilter}}</h2>
    <input type="text" v-model="text">
</div>
<script>
    let app = new Vue({
        el:'#app',
        data:{
            msg:'Vue.fileter 过滤器',
            text:''
        }
    })
    //在全局设置 Vue构造器
    Vue.filter('myFilter',function(value){
        return '￥'+value+'元';
    })
</script>
<!--http://localhost:63342/htdocs/Feweb/%E6%BD%AD%E5%B7%9E%E4%BD%9C%E4%B8%9A/%E8%BF%BD%E6%A2%A6%E8%80%81%E5%B8%88/Vue/%E5%85%A8%E5%B1%80API/Vue.fileter.html?_ijt=254ifgut5kha21sqfrcbo6fcta-->
```

##### Vue.component

```html
<div id="app">
    <hd-nav></hd-nav><!--小写-->
</div>
<!--全局组件-->
<script>
    Vue.component(
    	'hdNav',
        {
            template:`<h2 style="color: skyblue">全局组件</h2>`
        }
    )
    new Vue({
        el:'#app'
    })
</script>
<!--局部组件-->
<script>
    new Vue({
        el:'#app',
        //组件声明
        components:{
            hdNav:{//驼峰命名
                template:`<h2 style="color: hotpink">局部组件</h2>`
            }
        }
    })
</script>
```

##### 选项模板

```html
<div id="app"></div>
<script>
    new Vue({
        el:'#app',
        template:`<h2 style="color: hotpink">选项模板</h2>`
    })
</script>
<!--效果地址：http://localhost:63342/htdocs/Feweb/潭州作业/追梦老师/Vue/全局API/选项模板.html?_ijt=grl3pruolnu2u6mkbq2ekkv7tm-->
```

##### 标签模板

```html
<div id="app"></div>
<template id="tpl">
	<h2 style="color:hotpink">
        标签模板
    </h2>
</template>
<script>
    new Vue({
        el:'#app',
        template:'#tpl'
    })
</script>
<!--效果地址：http://localhost:63342/htdocs/Feweb/%E6%BD%AD%E5%B7%9E%E4%BD%9C%E4%B8%9A/%E8%BF%BD%E6%A2%A6%E8%80%81%E5%B8%88/Vue/%E5%85%A8%E5%B1%80API/vue.nextTick.html?_ijt=5mdn8k667kh09fegoaeudpuom4-->
```

##### component父组件传递数据给子组件

```html
<!--谁用谁 就是 父组件
	谁被谁用 就是 子组件
-->
<div id="app">
    <hd-nav title="商品列表" main-title="主标题" :alt="msg"></hd-nav>
</div>
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
<script>
    new Vue({
        el:'#app',
        data:{
            msg:"Hello World!"
        },
        components:{
            hdNav:{
                template:`<h2>选项组件 - {{title}} - {{mainTitle}} - {{alt}}</h2>`,
                // props 用于接收父组件的数据
                props:['title','mainTitle','alt']
            }
        }
    })
</script>
<!--
	效果地址：http://localhost:63342/htdocs/Feweb/%E6%BD%AD%E5%B7%9E%E4%BD%9C%E4%B8%9A/%E8%BF%BD%E6%A2%A6%E8%80%81%E5%B8%88/Vue/%E5%85%A8%E5%B1%80API/component%E7%88%B6%E7%BB%84%E4%BB%B6%E4%BC%A0%E9%80%92%E6%95%B0%E6%8D%AE%E7%BB%99%E5%AD%90%E7%BB%84%E4%BB%B6.html?_ijt=vf5pbaut0chg1gnsvtpnpthmqf
-->
```

##### 父组件引用子组件

```html
<div id="app">
    <hd-nav title="商品列表" main-title="主标题" :alt="msg"></hd-nav>
</div>
<script>
    let child = {
        template:`<em> child组件</em>`
    }
    let parent = {
        template:`
			<h2>选项组件 - {{title}} - {{mainTitle}} - {{alt}}
				<child></child>
    		</h2>
		`,
        props:['title','mainTitle','alt'],
        components:{
            child:child
        }
    }
    new Vue({
        el:"#app",
        data:{
            msg:"Hello World!"
        }
    })
</script>
```

