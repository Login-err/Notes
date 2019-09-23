for in遍历的是数组的索引(即键名)，而for of遍历的是数组的元素值

例：

for in //将所有的属性名遍历出来  

```js
var arr = ['nick','freddy','mike','james'];
	for(var item in arr){	
		console.log(item);//1,2,3,4
	}
```
```javascript
var man = {
    age:18,
    name:"fqn",
    marry:false,
    sex:"gril"
}
for(var key in man){
    console.log(key,":",man[key]);
}
//age:18
//name:fqn
//marry:false
//sex:gril
```

for of

```javascript
var arr = [
	{ name:'nick', age:18 },
	{ name:'freddy', age:24 },
	{ name:'mike', age:26 },
	{ name:'james', age:34 }
];
for(var item of arr){	
	console.log(item.name,item.age);
}
```

输出结果：

```
nick 18

freddy 24

mike 26

james 34
```





for of 无法遍历对象

```javascript
var userMsg = {
	nick: {
		name: 'nick',
		age: 18,
		sex: '男'	
	},
	freddy: {
		name: 'freddy',
		age: 24,
		sex: '男'
	}	
};

for(var i1 in userMsg){
	console.log(i1);	
	for(var i2 in userMsg[i1]){
		console.log(i2+': '+userMsg[i1][i2]);
	}
}
console.log('-----------分割线-----------');
for(var item of userMsg){	
	console.log(item);
}
```

输出结果：

![img](https://img-blog.csdn.net/20180531124821466?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3czOTAwNTg3ODU=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

遍历输出的结果不一样

```javascript
var arr = ['nick','freddy','mike','james'];
for(var i in arr){
	console.log(i);	
}
console.log('-----------分割线-----------');
for(var item of arr){	
	console.log(item);
}
```

![img](https://img-blog.csdn.net/20180531123759812?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3czOTAwNTg3ODU=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

