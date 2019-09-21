##### 什么是svg

###### svg指可伸缩矢量图形（即放大和缩小画质不会发生变化）

###### svg用来定义用于网络的基于矢量的图形

##### 区别于canvas

###### canvas大部分的样式都是基本的api

###### svg写在标签里面的内容，基于标签的属性来实现样式





##### svg

```html
<!--
	跟canvas一样，如果需要定义svg的画布宽高，直接定义属性的宽高
	xmlns:引入标准
-->
<!--  绘制圆 -->
<svg xmlns="http://www.w3.org/2000/svg" width="100%" height="100%">
	<!--
	cx,cy 圆心坐标  r 半径  fill 填充颜色(默认为黑)  stroke 绘制颜色 stroke-width:10 线宽
	fill如果不需要填充颜色的时候：
		fill:transparent/none
-->
    <circle cx='250' cy='250' r='100' fill='red' stroke='blue'></circle>
	<circle cx='250' cy='250' r='100' style="fill:'red';stroke:'blue';"></circle>
</svg>

<!-- 绘制椭圆 -->
<svg xmlns="http://www.w3.org/2000/svg" width="100%" height="100%">
	<!--
	cx,cy 圆心坐标 rx 属性定义的水平半径 ry 属性定义的垂直半径 fill 填充颜色(默认为黑)  stroke 绘制颜色 stroke-width:10 线宽
-->
    <ellipse cx='250' cy='250' r='100' fill='red' stroke='blue'></ellipse>
</svg>

<!-- 绘制椭圆 -->
<svg xmlns="http://www.w3.org/2000/svg" width="100%" height="100%">
	<!--
	width height 宽高 坐标x，y 圆角 rx，ry  fill 填充颜色(默认为黑)  stroke 绘制颜色 stroke-width:10 线宽
-->
    <rect width='250' height='250' x='100'  y='100' fill='red' stroke='blue'></rect>
</svg>

<!-- 绘制线条 -->
<svg xmlns="http://www.w3.org/2000/svg" width="100%" height="100%">
	<!--
	line：线条
		x1，y1
		x2，y2
		stroke-opacity 透明
		fill-opacity
		fill 填充颜色(默认为黑)  stroke 绘制颜色 stroke-width:10 线宽
-->
    <line x1='250' y1='250' x2='100'  y2='100' fill='red' stroke='blue'></line>
</svg>

<!-- 绘制折线 -->
<svg xmlns="http://www.w3.org/2000/svg" width="100%" height="100%">
	<!--
	line：线条
		point
		stroke-opacity 透明
		fill-opacity
		fill 填充颜色(默认为黑)  stroke 绘制颜色 stroke-width:10 线宽
		fill-rule 填充规则 evenodd/nonzero
-->
    //衔接处不闭合
    <polyline point='50 50 100 100 150 50 200 100' fill='red' stroke='blue'></polyline>
    //衔接处自动闭合
    <polygon point='50 50 100 100 150 50 200 100' fill='red' stroke='blue'></polygon>
</svg>
```

##### g标签

```html
<svg xmlns="http://www.w3.org/2000/svg" width="100%" height="100%">
    <g transform='translate(250,250)' fill='red' stroke='blue'>
    <circle r='50' ></circle>
    <circle r='100'></circle>
    <circle r='150'></circle>
    <circle r='200'></circle>
    </g>
</svg>


<!--
	d属性 
		M（起始坐标），
		L（结束坐标），
		H（水平线），
			大写的H是坐标位置
			小写的h是长度
			取值可以正值，可取负值， 取负值的时候等于取反方向【发坐标】
		V（垂直线），
			同上
		A（圆弧），
			A命令 x半径 y半径 角度 弧长（0 小弧 1 大弧） 方向（0 逆时针 1顺时针）
		C命令：
			三次贝塞尔曲线（x1，y1，x2，y2，x，y） x1，y1控制点一 x2，y2控制点二 结束点x，y
		S命令：
			平滑贝塞尔曲线 自动对称一个点（x2，y2，x，y）x2，y2控制点 结束点x，y
		Q命令：
			二次贝塞尔曲线（x1，y1，x，y） x1，y1控制点二 结束点x，y
		T命令：
			一次贝塞尔（就是一条直线） （x，y）
Z（闭合路径）
-->
<svg xmlns="http://www.w3.org/2000/svg" width="100%" height="100%">
    <path d='M50 50 L150 150 L250 150Z' style=''></path>
    <path d='M50 50 L150 150 L250 150H300'></path>
</svg>
```

```html
<!-- 
	text字体：
		x，y是字体坐标
		font-size文字大小
		text-anchor文字左中右偏移（start middle end）
-->
<svg xmlns="http://www.w3.org/2000/svg" width="100%" height="100%">
   <text x='250' y='250' font-size='50' text-anchor='start'>黄黄黄黄</text>
</svg>

<!-- 
	image：
		x，y是图片坐标
		xlink:href
-->
<svg xmlns="http://www.w3.org/2000/svg" width="100%" height="100%">
   <image x='250' y='250' xlink:href='url'>黄黄黄黄</image>
</svg>
```

##### use可以增加样式 

```html
<--user配合defs/symbol使用-->
<svg xmlns="http://www.w3.org/2000/svg" width="100%" height="100%">
    <defs>
    	<g>
        	<circle id="circle" cx='50' cy='50' r='50'></circle>
        </g>
    </defs>
    <symbol></symbol>
    <use xlink:href='#circle'></use>
</svg>
```

