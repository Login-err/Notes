###### css选择器之[class*=col-]

```css
[class*=col-] //代表包含col-的类名，比如说col-4等都是可以匹配的
[class^=col-] //代表以col-开始的类名，比如说col-4是可以匹配的
[class$=col] //代表以col-结尾的类名，比如说a-col是可以匹配的
```



###### :nth-child()

```scss
/* 选择第n个，n位数字 */
.box:nth-child(n){};
/* 选择列表中的偶数标签 */
.box:nth-child(2n){};
//或者
.box:nth-child(even){}
/* 选择列表中的奇数标签 */
.box:nth-child(2n-1){};
//或者
.box:nth-child(odd){}
/* 选择前几个元素   【负方向范围】选择第1个到第6个 */
.box:nth-child((-n+6){};
/* 从第几个开始选择  【正方向范围】选择从第6个开始的，直到最后 */
.box:nth-child(n+6){};
/*两者结合使用，可以限制选择某一个范围 【限制范围】选择第6个到第9个，取两者的交集 */
.box:nth-child(-n+9):nth-child(n+6){};
/* 选择列表中的倒数第n个标签 n为数字 */
.box:nth-last-child(n){}
```

##### 文字竖着排列

```scss
writing-mode: vertical-rl;//给父容器添加
/*
    horizontal-tb：水平方向自上而下的书写方式。即 left-right-top-bottom
    vertical-rl：垂直方向自右而左的书写方式。即 top-bottom-right-left
    vertical-lr：垂直方向内内容从上到下，水平方向从左到右
    sideways-rl：内容垂直方向从上到下排列
    sideways-lr：内容垂直方向从下到上排列
*/
```

##### 对齐两端文本

```scss
/* 通过text-align-last:justify设置文本两端对齐 */
```

##### 去除无用属性

   ```scss
text-align-last:auto|left|right|center|justify|start|end|initial|inherit;
/*
	auto	默认值。最后一行被调整，并向左对齐
    left	最后一行向左对齐
    right	最后一行向右对齐
    center	最后一行居中对齐
    justify	最后一行被调整为两端对齐
    start	最后一行在行开头对齐（如果 text-direction 是从左到右，则向左对齐；如果 text-direction 是从右到左，则向右对齐）
    end	最后一行在行末尾对齐（如果 text-direction 是从左到右，则向右对齐；如果 text-direction 是从右到左，则向左对齐）
*/
   ```

###### 使用text-overflow控制文本溢出

```css
//单行文本控制溢出
.box{
    overflow:hidden;
    text-overflow:ellipsis;
    white-space:nowrap;
}
//多行文本控制溢出
.box{
    display:-webkit-box;
    overflow:hidden;
    text-overflow:ellipsis;
    -webkit-line-clamp:3;
    -webkit-box-orient:vertical;
}
//或
.box{
    overflow:hidden;
    position:relative;
    max-height:90px;
}
.box::after{
    position:absolute;
    right:0;
    bottom:0;
    padding-left:40px;
    background:linear-gradient(to right,transparent,#fff 50%);
    content:'...';
}
```

