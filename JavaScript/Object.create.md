##### Object.create() 创建一个对象   第一个参数是新产生的对象（即返回值）继承哪个对象，第二个参数是新对象添加的属性

```javascript
function Parent(name,sex){
    this.name = name;
    this.sex = sex;
}
const a = Object.create(Parent);
console.log(a.__proto__);//是Parent构造函数


const aa = Object.create(null,{a:1});
console.log(aa);//{a:1}  不会有__proto__
const bb = {a:1};
console.log(bb);//{a:1,__proto__:.....}  
```

