##### 浮动布局

> 浮动布局简介：当元素浮动以后可以向左或向右移动，直到它的外边缘碰到包含它的框或者另外一个浮动元素的边框为止。元素浮动以后会脱离正常的文档流，所以文档的普通流中的框就变现的好像浮动元素不存在一样。

###### 优点：

可以在图文混排的时候可以很好的是文字环绕在图片周围。另外当元素浮动起来之后，它的块级元素的一些性质例如可以设置宽高等，但它与inline-block还是有一些区别的，第一个就是关于横向排序的时候，float可以设置方向而inline-block方向是固定的，还有一个就是inline-block在使用时会有空白间隙的问题

###### 缺点：

浮动元素脱离文档流，就无法撑起父元素，会造成父级元素的高度塌陷

###### 清除浮动的方式：

1. 添加额外的标签

```html
<div class='parent'>
    // 添加额外的标签并且添加clear属性
	<div style='clear:both;'></div>
    // 也可以加一个br标签
</div>
```

2. 父级添加overflow属性，触发BFC盒模型，或者设置高度

```html
<div class='parent' style='overflow:hidden'>// auto也可以
    // 将父元素的overflow设置为hidden
    <div class='f'></div>
</div>
```

3. 建立伪类选择器清除浮动

```css
.parent:after{
    content:'';
    display:block;
    height:0;
    clear:both;
    /* 设置添加子元素看不见 */
    visibility:hidden;
}
```

##### 使用display：inline-block会产生什么问题

###### 两个display:inline-block元素放到一起回产生一段空白

产生原因：行内元素排版的时候，元素之间的空白符（空白、回车换行等）都会被浏览器处理，根据css中white-space属性的处理方式（默认是normal，合并多余空白），原来***HTML代码中的回车换行被转成一个空白符***，在字体不为0的情况下，空白符占据一定宽度，所以inline-block的元素之间就出现了空隙。

###### 解决办法

1. 将子元素标签的结束符和下一个标签的开始符写在同一行或把所有的子标签写在同一行
2. 父元素中设置font-size：0，在子元素上面重置font-size
3. 为子元素设置float：left；