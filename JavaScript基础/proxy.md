```javascript
/*
new Proxy(被代理的对象，{
	代理的行为
})
*/
let obj = {
    name:'heaven',
    age:18,
    sex:'male'
}
let proxy = new Proxy(obj,{})
console.log(proxy.name);// heaven
```

```javascript
/*
	get函数(被代理的对象，访问的属性)  当通过代理访问属性时触发
*/
let obj = {
    name:'heaven',
    age:18,
    sex:'male'
}
let proxy = new Proxy(obj,{
    get(){
        return 'abc'
    }
})
console.log(proxy.name);// abc
```

```javascript
let obj = {
    name:'heaven',
    age:18,
    sex:'male'
}
let proxy = new Proxy(obj,{
    get(target,prop){
        console.log(target,prop)
 		// return target[prop];// 返回代理对象的真实属性
    }
})
proxy.name;//{ name:'heaven',age:18, sex:'male'}  heaven
```

```javascript
let obj = {
    name:'heaven',
    age:18,
    sex:'male'
}
let proxy = new Proxy(obj,{
    get(target,prop){
        console.log(target,prop)
 		// return target[prop];// 返回代理对象的真实属性
    }
})
proxy.name = 'huanglian';
console.log(obj.name);// huanglian
```

##### set函数

```javascript
/*
	set函数(被代理的对象，设置的属性，设置的值)
		1.当通过代理设置属性时触发
		2.
*/
let obj = {
    name:'heaven',
    age:18,
    sex:'male'
}
let proxy = new Proxy(obj,{
    get(target,prop){
        console.log(target,prop)
 		// return target[prop];// 返回代理对象的真实属性
    }
    set(target,prop,value){
        if(target.hasOwnProperty(prop)){
            console.log(`${prop}属性已经存在，不能修改了`)
        }else{
            target[prop] = value
        }
	}
})
proxy.name = 'huanglian';
proxy.aaa = 'bbbbb';
console.log(obj.aaa);// bbbbb
console.log(obj.name);// huanglian
```

