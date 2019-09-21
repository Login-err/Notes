箭头函数没有this

```javascript
function a(a,b){
    console.log(x+y,this);
}
a(5,6);//11,window
a.call(document,5,6);//11,document
a.apply(document,[5,6]);//11,document  apply只能传两个参数 第二个参数以数组传入

document.onclick = function(){
    console.log(this);
}.bind({name:"黄炼"});
bind();//产生一个新函数
```

```javascript
let json = {
    a:3,
    b:4
};
function fn(){
    console.log(this,a+b)
}
fn.call();//window  NaN
fn.call(json);//json  7
fn.call(8,15);//Number{8}  NaN
call();//括号里面第一个是对象


apply();//只接受两个参数  第一个指向改变this指向的对象  第二个参数是接收数组
fn.apply(window,[2,3]);//window 5
fn.apply(json);//{a:3,b:4}  5

bind();//被动执行  传参形式与call一样
apply()  call();//主动执行
```

