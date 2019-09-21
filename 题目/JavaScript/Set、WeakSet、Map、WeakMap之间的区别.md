#### Set结构

##### Set是ES6给开发者带来的一种新的数据结构，你可以理解为值的集合。我们平时见到的数组Array也是一种数据结构，但是Set跟其他的数据结构的不同的地方在于，他的值不会有重复项

###### 基本用法

```javascript
//1.创建一个Set的结构
const s = new Set();
console.log(s);//Set{}

//2.创建含内容的Set结构
const s = new Set([1,2,3]);
console.log(s);//Set{1,2,3}

//3.创建出一个Set结构
const s = new Set();
//使用add方法添加成员
s.add(1);
s.add(2);
s.add(3);
console.log(s);//Set {1,2,3}
console.log(s.size);//3
console.log( s.delete(2) );//true
s.clear()
console.log(s);//Set {}
const ss = new Set(['a','b',3,4])
console.log( ss.has(3) );//true
console.log( ss.entries() );//SetIterator {"a" => "a", "b" => "b", 3 => 3, 4 => 4}
```

###### set的用途之一：数组去重

``const arr = [1,2,3,3,4,5,4] const s = new Set(arr);   console.log(s);//set {1,2,3,4,5  const newArr = Array.from(s)};console.log(newArr);//[1,2,3,4,5]   ``



#### WeakSet

##### WeakSet与Set的不同点就是WeakSet里面的值必须是对象，其次，WeakSet 中的对象都是弱引用，即垃圾回收机制不考虑 WeakSet 对该对象的引用，也就是说，如果其他对象都不再引用该对象，那么垃圾回收机制会自动回收该对象所占用的内存，不考虑该对象还存在于 WeakSet 之中。WeakSet 没有遍历操作（ 即没有key()、 values() 和entries() 方法）， 也没有size属性； 二是无法清空， 即不支持clear方法。WeakSet 只有四个方法可用： get()、 set()、 has()、 delete()。

```javascript
const weak = new WeakSet({name:'huanglian'})
```







#### Map

##### Map对象是一种有对应键/值对的对象，Map所含有的方法与Set几乎一样

 #### WeakMap

##### WeakMap的设计目的在于， 键名是对象的弱引用（ 垃圾回收机制不将该引用考虑在内）， 所以其所对应的对象可能会被自动回收。 当对象被回收后， WeakMap自动移除对应的键值对。基本上， WeakMap的专用场合就是， 它的键所对应的对象， 可能会在将来消失。 WeakMap结构有助于防止内存泄漏。

##### WeakMap 与 Map 在 API 上的区别主要是两个， 一是没有遍历操作（ 即没有key()、 values() 和entries() 方法）， 也没有size属性； 二是无法清空， 即不支持clear方法。WeakMap只有四个方法可用： get()、 set()、 has()、 delete()。

####        Set

* 成员不能重复

- 只有健值，没有健名，有点类似数组。

- 可以遍历，方法有add, delete,has

  #### weakSet

* 成员都是弱引用，随时可以消失。 可以用来保存DOM节点，不容易造成内存泄漏

* 不能遍历，方法有add, delete,has

* 成员都是对象

  #### Map

* 本质上是健值对的集合，类似集合

* 可以遍历，方法很多，可以干跟各种数据格式转换

  #### weakMap

* 健名所指向的对象，不计入垃圾回收机制

* 不能遍历，方法同get,set,has,delete
* 直接受对象作为健名（null除外），不接受其他类型的值作为健名