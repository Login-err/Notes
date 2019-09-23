---
title: BOM
date: 2019/1/27
catetories: JS
---



## BOM：浏览器对象模型

window对象——window对象是js中的顶级对象,所有定义在全局作用域中的变量，函数都会变成window对象的属性和方法，在调用时可省略window

```javascript
 window.open(url,target,param);
//url 要打开的地址
//target 新窗口的位置
//param 新窗口的一些设置
```

#### window对象

######  	定时器：

```javascript
var set = setTimeout(function(){},3000)；//在3秒后执行function函数
clearTimeout(set);//取消定时器
var set = setInterval(function(){},3000)//每隔3秒执行一次function函数 
clearInterval(set);//取消定时器
```

###### 	offset：

```html
<style>
    #{
        width:400px;
        height:100px;
        border:1px solid #ccc;
    }
</style>
<div id="wrap"></div>
<script>
	var oWrap = document.getElementById("wrap");
    console.log(oWrap.offsetWidth);//offsetWidth = border-left + padding-left + width + padding-right + border-right
    console.log(oWrap.offsetLeft);//offsetLeft = oWrap的左边框到浏览器左边缘的距离
    oWrap.offsetParant;//放回离oWrap最近带有定位的父级元素
</script>
```

