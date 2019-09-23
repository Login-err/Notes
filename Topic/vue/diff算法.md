diff可是逐层比较的

首先旧的虚拟dom是根据真实的Dom生成的，然后当虚拟dom的某个节点的数据发生变化后会产生一个新的Vnode，发现有什么不一样的地方直接修改到真实的dom上，然后是oldVnode的值为Vnode，diff算法的过程就是调用名为patch的函数，比较新旧节点，一边比较一边给真实的dom打补丁( 在采取diff算法比较新旧节点的时候，比较只会在同层级进行, 不会跨层级比较。)

虚拟dom（伪代码）

```
var Vnode = {
	el:''
    tag: 'div',
    children: [
        { tag: 'p', text: '123' }
    ]
};
```

一个patch函数传入新旧节点，然后判断哪个节点是否值得比较（如果标签，类名，key值等不同就不值得比较，直接新节点替换旧节点，），在值得比较的情况下，会存在几种情况，首先，给Vnode的el绑上oldVnode的el值，且给el变量（其实这el变量就是真实的dom）赋上oldVnode的el值，然后判断两个Vnode与oldVnode是否相等，如果相等，直接return；然后再判断两者都有文本节点，且不相等，那么el的文本节点设置为Vnode的文本节点；如果oldVnode有子节点，而Vnode没有，那么直接删除el的子节点；如果oldVnode没有子节点，然后Vnode有，那么将Vnode的子节点添加到el上；如果两者都有，则执行updateChildren的函数比较子节点（这一步很重要）;

updateChildren函数的作业

首先将Vnode的子节点和oldVnode子节点提取出来了，Vnode的子节点为Vch，oldVnode的子节点为oldCh.oldCh和vCh各有两个头尾节点StartIdx和EndIdx，他们的两个变量相互比较，有四个比较方式，如果设置了key，就会利用key进行比较