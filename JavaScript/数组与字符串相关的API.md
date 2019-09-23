```javascript
//push
	//参数：任意数据
	//功能：直接改变原数组，给数组添加参数数据
	//返回值：返回改变后的数组长度值
//pop
	//参数：不需要参数，传进去也没有用
	//功能：改变原数组，删除最后一位
	//返回值：删除了谁返回谁
//shift
	//删除数组第一个
//unshift
	//向数组第一个增加第一个
var a = ["james","duncan","kobe"];
a.push("green","durant");//往数组后面加内容  运行完返回改变后的数组长度
console.log(a);//james,duncan,kobe,green.durant
var b = ["james","duncan","kobe"];
b.pop();//往数组后面删内容  
console.log(b);//james,duncan 
```

```javascript
var a = [1,2,3,4,5,6,4,5,21,2]
var f= a.slice(3,4);//5
```

```javascript
var a = ["james","duncan","green"];
a.splice(2);
a.splice(1,1);//第一个参数：从哪个位置开始  第二个参数：切几个
a.splice(1,1,"manu");//第三个参数：添加
console.log(a);//["james","duncan"]
```

```javascript
//sort升序排列
//reverse反序排列
sort(function(a,b){
    return 99;//返回正值就交换位置
})//函数里面可以自定义排列方式
返回值与排序后的a的值一模一样
var a = [12,23,54,12,65,32,454];
a.sort();//升序
console.log(a);//12,12,23,32,54,65,454
var b = [12,23,54,12,65,32,454];
b.reverse();//反序
console.log(b);//454,32,65,12,54,23,12
```

```javascript
//concat数组的拼接
var a = [1,2,3];
var b = [4,5,6];
var c = a.concat(b);
console.log(c);//[1,2,3,4,5,6]  不改变a，b
```

```javascript
//isArray();判断是不是数组  通常用在对类数组的判断
var a = [1,2];
console.log(Array.isArray(a));//true
```

```javascript
//join将字符串或者数组的拼接
var a = [1,2,3];
var b = a.join("<==>");
console.log(b);//1<==>2<==>3
```

```javascript
//includes
var a = "hello world";
a.includes("hello");//true
a.includes("hello,2");//false  2是起始的位置
```

##### 字符串相关的API

###### 截取字符串

```javascript
var a = "12黄炼5646";
var b = a.subString(2,4);
var bb = a.subString(4,2);
var c = a.subString(2);
var d = a.subString(-2,2);
var e= a.slice(-2,-5);//slice()方法还可以用在数组上面不只是在字符串上
var f= a.slice(-5,-2);
console.log(b);//黄炼
console.log(bb);//黄炼
console.log(c);//黄炼5646
console.log(d);//12 将-2理解成0
console.log(e);//无结果 
console.log(f);// 炼56
```

###### 查询

```javascript
var fruits = ["Banana","Orange","Apple","Mango","Banana","Orange","Apple"];
var a = fruits.indexOf("Apple",4);
var b = fruits.indexOf("james");
console.log(a);//6
console.log(b);//-1 找不到返回-1

var arr = new Array(3)
arr[0] = "George"
arr[1] = "John"
arr[2] = "Thomas"

var arr2 = new Array(3)
arr2[0] = "James"
arr2[1] = "Adrew"
arr2[2] = "Martin"
console.log(arr.concat(arr2))//George,John,Thomas,James,Adrew,Martin
```

###### 字符串变大小写

```javascript
var a = "aBc"
var b = "a.toLocaleUpperCase()";
var c = "a.toLocaleLowerCase()";
console.log(b);//ABC
console.log(c);//abc
```

###### 字符切割

```javascript
var a  = "james,kobe,duncan,green";
var b = a.split(",");//切完变成四个人的名字
console.log(b);//["james","kobe",]
```

