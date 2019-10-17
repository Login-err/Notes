```javascript
// 引用express模块
const express = require('express');
const app = express();// 创建服务
app.use(express.static('public'));// 1.自动为public下面的文件设置路由  2.自动把public目录下的index.html设置为首页
app.listen(3000);// 相对于之前的server.listen
```

```javascript
const express = require('express');
const app = express();
/*
	app.get(路由，回调函数)
		回调函数在符合指定路由并且是get方式请求时触发
    app.post(路由，回调函数)
    	回调函数在符合指定路由并且是post方式请求时触发
*/
app.get('login',(req,res)=>{
    res.end('login')
});
app.post('login',(req,res)=>{
    res.end('login');
})；
// app.use无论是get还是post都可以触发

// 数据之间存放在req.query	
app.use('/login',(req,res)=>{
    console.log(req.query);//
    res.end('login')
})
```

```javascript
const express = require('express');
const app = express();
app.get('/:number',(req,res)=>{
    console.log(req.params.number);
    res.send([1,2,3]);
    res.render('showResult',{
        result:result
    })
})
app.use(express.static('public'));
app.listen(5000);

/*
	res.params.变量  这个对象储存了对应的路由规则：变量后面的值
	res.send(数据)  作为结束响应的标志（与end不同的是他不仅能传递字符串和buffer数据，他也可以传递数组等数据）
	res.render('url',data) 专门用来views目录下的ejs页面
	ejs是后台模板
	1. 可以在<% js代码 %>
	2. 可以在<% =变量 %>
	ejs可以通过<%- include('path') %>引入公共部分
*/
```

