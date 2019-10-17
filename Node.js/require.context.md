```javascript
const path = require('path');
const name1 = path.basename('aaa/component/huanglian.vue', '.vue');
const name2 = path.basename('aaa/component/huanglian.vue');
const name3 = path.basename('aaa/component/', '.vue');
console.log(name1); // huanglian
console.log(name2); // huanglian.vue
console.log(name3); // component
```



```javascript
/*
	{directory} String 搜索文件夹的目录
	{useSubdirectories} Boolean true 包含directory的子目录 false 不包含子目录
	{regExp} RegExp 文件夹名匹配的正则
*/
const file = require.context(directory, useSubdirectories, regExp);
/*
	require.context模块导出（返回）一个（require）函数，这个函数可以接收一个参数：request 函数–这里的 request 应该是指在 require() 语句中的表达式
*/
/*
	这里导出的file有三个属性： resolve，keys，id
	resolve 是一个函数，它返回请求被解析后得到的模块 id。
	keys 也是一个函数，它返回一个数组，由所有可能被上下文模块处理的请求组成。
	id 是上下文模块里面所包含的模块 id. 它可能在你使用 module.hot.accept 的时候被用到		
*/
```

##### Vue全局组件

```javascript
const requireAll = context => context.keys().map(context);
const component = require.context('./components', false, /\.vue$/);
requireAll(component).forEach( ({dafault: item}) => {
    console.log(item);
    Vue.component(item.name, item)
})
```

##### 利用require.context遍历目录所有的图片（文件的目录为assets/kittens）

```vue
<template>
	<div id="app">
        <img src"@/assets/logo.png">
        <li v-for="item in images">
            <h3>Image: {{ item }}</h3>
    		<img :src="imgUrl(item)">
    	</li>
    </div>
</template>
<script>
	const imagesContext = require.context('@/assets/kittens/', false, /\.jpg$/)
	console.log(imagesContext);
    console.log(imagesContext('./kitten1.jpg'));
    console.log(imagesContext.keys());
    export default {
        created: function () {
            this.images = imagesContext.keys();
        },
        name: 'haha',
        data () {
            return {
                images: [],
                msg: 'Welcome to Your Vue.js App'
            }
        },
        methods: {
            imgUrl: function (path) {
                console.log('path:'+path);
                return imagesContext(path);
            }
        }
    }
</script>
```

