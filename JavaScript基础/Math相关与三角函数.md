##### Math相关

```javascript
//π的值
var a = Math.PI
//绝对值
var a = -1;
var b = Math.abs(a);
console.log(a,b);//-1,1
//求次方
Math.pow(2,3);//2^3 
Math.pow(16,1/2);//4
Math.pow(0,0);//1
Math.pow(5,0);//1
Math.pow(256);//NaN
//求1/2
Math.sqrt(256);//16
//向下取整
Math.floor(5.2);//5
Math.floor(-2.5);//-3
//向上取整
Math.ceil(2.2);//3
Math.ceil(-2.1);//-2
//四舍五入
Math.round(4.49);//4
Math.round(4.51);//5
Math.round(-4.51);//-5
```

```JavaScript
//正弦值
Math.sin(Math.PI/6);//0.499999999 = 0.5
//余弦值
Math.cos(Math.PI/3);//0.500000001 = 0.5
//正切值
Math.tan(Math.PI/4);//0.999999999 = 1
//反三角函数
Math.asin(0.5);//0.52359877 = Math.PI/6
```

##### 随机数

```javascript
Math.random()//随机数生成  返回一个0到1的数
```

