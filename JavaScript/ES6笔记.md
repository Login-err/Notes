console.log(a);

var a;(var 具有变量提示的特性)

( 不过可以使用 var a = !a;(给a赋予!a的值 a=true) )

a的结果为undefined

如何把var换成let ，则会报错，因为let不具有变量提升的效果

var a = 1;

var a = 2;(程序不会报错，但是会覆盖之前给a赋的值)

let的话，则会报错，因为let具有暂时性死区----块作用域(ES6新增)

（ES5具有全局作用域和函数作用域）（**块作用域**里面ES6不允许相同的变量名）

let a =1;
(function(){
​	console.log(a);
​	let a =2;
})()     ————(会报错，假如把let a =2注释掉，则正常运行，a=1)



function foo(){

​	console.log(a);

​	if(false){

​		var a =2;

​	}

}(函数输出a=2，由于是函数，所以先定义；如果改成let，则会报错)

const 常量只允许定义一次，不允许重复复值，但是数组和对象可以修改

#### 拓展运算符的用途:（浅复制）

##### 1.合并数组

```javascript
arr1.push(...arr2);//把arr2合并到arr1后面
arr2.unshift(...arr1);//把arr1合并到arr2前面

//或者
var arr1 = ["two","three"];
var arr2 = ["one",...arr1,"four","five"];
```

##### 2.复制数组

```
var arr = [1,2,3];
var arr2 = [...arr];
console.log(arr2);//1,2,3
```

##### 3.结构赋值

```javascript
var {x,y,...z} = {x:1,y:2,a:3,b:4};
console.log(x);//1
console.log(y);//2
console.log(z);//{a:3,b:4}
```

##### 4.函数传参

```javascript
var arr1 = ["a","b","c"],
    arr2 = ["d","e","f"];
function foo(a,b,c){
    console.log(a,b,c);
}
foo(...arr1);//1,2,3
var arr3 = [...arr1,...arr2];//a,b,c,d,e,f
```

##### 5.将字符串变成数组

```javascript
var arr = [..."hello",..."my","world"];
console.log(arr);//输出arr["h","e","l","l","e","m","y","world"];
```

