```javascript
var arr = new Array();
arr[0] = "James";
arr[1] = "Kobe";
arr[2] = "Duncan";
arr.unshift("Curry");//向数组前面添加一个或多个元素   输出Curry,James,Kobe,Duncan
arr.push("Green");//向数组末尾添加一个或多个元素  输出James,Kobe,Duncan,Green
arr.slice(1,2);//输出kobe  从已有的数组中返回选定的元素
arr.slice(start,end);//start必选，end可选
```

```javascript
var arr = [..."hello","world"];
arr.find(function(item.key){console.log(item,key)})//
arr = ["h","e","l","l","e","world"];
// h,0
// e,1
// l,2
// l,3
// e,4
// world,5
//当遇到return时就结束
arr.find((function(item.key){
    console.log(item,key);
    return turn;
})//当遇到return放回true的时候 结束find函数
// h,0
var findData = arr.find(function(item){
    console.log(item);
    if(arr.length>1){
        return true;
    }
});
//放回world,如何没有满足这个条件的话则会返回undefined


findIndex(item)//返回下标
```

```javascript
var arr = ["Ade","Deranz","Gay","Mills"]
arr.fill(value,start,end);
var nArr = arr.fill("Manu",1,3);
console.log(nArr);//Ade,Manu,Manu,Mills
```

```javascript
var div = document.querySelectorAll("div");
Array.from(oDiv);//将类数组转换成数组
//或者
var oDiv = [...div];
```

```javascript
console.log(Object.is(NaN === NaN));//true
console.log(NaN === NaN);//false
Object.is([], []);// false
Object.is(0, -0);// false
Object.is(NaN, 0/0);// true
Object.is(NaN, 0);// false
```

```javascript
var obj1 = {
    a:0,
    b:1,
    c:2
};
var obj2 = {
    d:3,
    e:4
};
var obj3 = Object.assign(obj1,obj2,{
    f:6,
    g:7
});
console.log(obj3);//Object{a:0,b:1,c:2,d:3,e:4,f:6,g:7}
```

```javascript
var json = '{
	"result":true,
	"count":42
}';
var obj = JSON.parse(json);
console.log(obj);//Object{result:true,count:42}  将字符串转化为JSON格式
JSON.parse('{}');              // {}
JSON.parse('true');            // true
JSON.parse('"foo"');           // "foo"
JSON.parse('[1, 5, "false"]'); // [1, 5, "false"]
JSON.parse('null');            // null
JSON.parse('1');               //  1
```

```JavaScript
parseInt("123asdew");//123
parseInt("ab123");//NaN
parseInt("ff",16);//十六进制  255
f*16+f = 15*16+15
```

```javascript
parseFloat("12.3");//12.3
parseFloat({});//NaN  对象返回NaN
```

```javascript
var obj = {
    toString(){
        return 123;
    }
}
parseInt(obj);//123
```

