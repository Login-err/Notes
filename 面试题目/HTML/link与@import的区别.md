#### 区别

* link是HTML标签，@import是css提供的
* 页面加载时，link会同时被加载，而[@import](https://github.com/import)引用的CSS会等页面被加载完后再加载。 
* link没有兼容性问题，@import不兼容ie5以下
* link可以通过js操作dom动态引入样式表改变样式，而@import不可以

