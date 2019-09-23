---
title: Ajax
date: 2019/1/27 13:05:10
catetories: JS
---



#### ajax发送请求

##### 异步的JavaScript和xml

###### 特点：

* 无刷新页面的情况下，实现与后台的数据交互，同时在页面进行更新跨域：

* 不允许跨域请求

* 前端进行请求数据，后端说的算

* 和后端进行数据交互，需要在电脑上安装 集成环境（本地服务器）

```javascript
var ajax = new XMLHttpRequest();
//解决兼容性问题:
var ajax = null；
if(XMLHttpRequest){
    ajax = new XMLHttpRequest();
}else{
    ajax = new ActiveXObject('Microsoft.XMLHTTP');
    //解决ie兼容性问题
}

//post请求：
ajax.open('post',url,true);//true默认为异步请求
ajax.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded;charset=utf-8');
ajax.send("要传输的数据");
//get请求：
ajax.open('get',url,true);
ajax.send(null);

ajax.onreadystatechange = function(){
  	if(ajax.onreadyState == 4 && ajax.Status == 200) 
    {
        JSON.parse(ajax.response);
        //由于服务器返回的数据都是字符串，因此得转成json格式的值
	}
}
0--4
	0 初始化状态 ajax对象已被创建
    1 open()方法 已调用
    2 send()方法 已调用
    3 所有的响应 已经收到
    4 http 响应已经完全接收
    
后端返回前端都是字符串
echo json_encode($arr);//编译成字符串
//php每句语法都得;结束

后端解决跨域问题
header('Access-Control-Allow-Origin:*')
```

