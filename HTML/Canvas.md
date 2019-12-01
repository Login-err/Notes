---
title: Canvas
catetories: JS
date: 2019/1/27
---

##### canvas的宽度应该在canvas里面设置，不然到时绘制线条线条宽度不正确。canvas默认为inline

```javascript
var oCan = document.querySelector("canvas");
oCan.getContext("2d");//将canvas绘制区域变成2d,2d是当前唯一的合法值
oCan.beginPath();//开始一条路径或重置当前的路径
OCan.fillStyle();//改变颜色样式

//绘制路径
OCan.arc(this.x,this.y,this.r,0,Math.PI*2);//绘制圆的参数  x轴 y轴 圆半径 起始角度 结束角度(弧度值);
oCan.moveTo(x,y);//起始点的坐标
oCan.lineTo(x,y);//结束点的坐标
oCan.fill();//填充一块区域
oCan.stroke();//画出一块区域的边界
oCan.quadraticCurveTo(x1,y1,x2,y2);//控制点的坐标   结束点的坐标 与moveTO()方法搭配使用
oCan.bezierCurveTo(x1,y1,x2,y2,x3,y3);//控制点1的坐标  控制点2的坐标 结束点的坐标 与moveTO()方法搭配使用
ctx.arcTo(x1,y1,x2,y2,r);//创建弧 起始点坐标 终点坐标 弧半径
```

![弧/曲线](https://www.w3school.com.cn/i/arc.gif)

```html
<body>
    <canvas></canvas>
    <!--默认canvas大小为宽300，高150-->
</body>
<script>
    var oCan = document.querySelector("canvas");
    var cxt = oCan.getContext("2d");//将canvas绘制区域变成2d,2d是当前唯一的合法值
    //绘制矩形
    cxt.rect(x, y, w, h);//这里的宽高是按照默认宽高的比例,
    cxt.rect(100,100,50,50);//如果想在canvas为500高，300宽里面绘制该矩形，那么不能给canvas设置500px宽，300px高的样式，只能在canvas里面设置属性<canvas width="500" height="300"></canvas>只能这样，不然矩形会变形
    cxt.stroke();//绘制出该矩形,绘制边框线
    cxt.strokeStyle = "#fff";//与fillStyle一样
    cxt.lineWidth = "15px";//绘制边框线的宽度 从rect中的x位置开始向左右两边渲染，如果是基数的话 除二会存在0.5，由于0.5渲染不出来，会补充0.5，及15变成16px 默认边框线为2px
    cxt.fill();//默认填充黑色
    cxt.fillStyle = "#fff";//填充颜色 需加cxt.fill();
    cxt.strokeRect(100,100,50,50);//与上面两行代码等价
    cxt.fillRect()//实行矩形，这个不需要cxt.stroke()
    cxt.clearRect(x,y,w,h);//清除的坐标(x,y)清除的大小宽w，高h
    
    cxt.moveTo(x,y);//起始点
    cxt.lineTo(x,y);//绘制的路径
    
    cxt.beginPath();//产生作用域 不会与其他作用域发生样式覆盖  一般在写一个案例的时候都会添加它，防止将前面的样式覆盖
    cxt.closePath();//自动闭合， 不需要回到起始点的lineTo()
    
    
    cxt.lineJoin = "round";//边角是有一定的圆弧的
    cxt.lineJoin = "bevel";//边角是有一定的平直
    
    cxt.lineCap = "round";//端点有一定圆弧
    
    //绘制圆形
    cxt.translate(0,0);//参考点设置
    cxt.arc(x,y,r,x1,y1,bool);//x,y圆心坐标 r圆半径 x1起点弧度值 y1终点弧度值 bool顺时针还是逆时针 false顺时针

    cxt.rotate(rad);//rad弧度值  旋转图形  旋转中心点为左上角
   
    cxt.scale(1,1);//等比例缩放  分别对应宽高
    
    
    //使其成为一个独立的路径 相互之间不会影响 相当于一个作用域
    cxt.save();
    cxt.restore();
</script>
```

```javascript
//绘制图片/音频
var oCan = document.getElementsByTagName("canvas")[0];
var cxt = oCan.getContext("2d");
var img = new Image();
img.src = "..."
img.onload = function(){
    cxt.drawImage(img,0,0,350,400);//img绘制的图形，绘制起始点的坐标，绘制图形的宽高
    cxt.drawImage(img,0,0,350,400,200,200,150,150);//前面五个参数同上，后面：将前面绘制出来的图片移动到的坐标  绘制后的图片大小
    requestAnimationFrame('function');// 音频
}
```

```javascript
var oCan = document.getElementsByTagName("canvas")[0];
var cxt = oCan.getContext("2d");
var img = new Image();
img.src = '1.png';
img.onload = function(){
    var bgi = cxt.createPattern(img,'no-repeat/repeat/repeat-x')
    cxt.fillStyle = bgi;
    cxt.drawImage(img,0,0,500,500)
}
```



```javascript
//颜色渐变
//线性渐变（是某个角度 渐变到另一个角度） 
var oCan = document.getElementsByTagName("canvas")[0];
var cxt = oCan.getContext("2d");
var color = cxt.createLinearGradient(0,0,500,500);从（0,0）开始到（500,500）结束
color.addColorStop(0,"blue");
color.addColorStop(0.5,"red");
color.addColorStop(1,"green");
cxt.fillStyle = color
cxt.fillRect(0,0,500,500)
//径向渐变（是某个点 向四周扩散） 
```

```javascript
//颜色透明
var oCan = document.getElementsByTagName("canvas")[0];
var cxt = oCan.getContext("2d");
cxt.globalCompositeOperation = 'destination-out/source-over/destination-over'
```



```javascript
//绘制文本属性 
var oCan = document.getElementsByTagName("canvas")[0];
var cxt = oCan.getContext("2d");
var str = "canvas绘制的文本"
cxt.font = "30px 微软雅黑"
cxt.strokeText(str,x,y)//绘制空心文本
cxt.fillText(str,x,y)//绘制实心文本
cxt.measureText(str).width//获取文本宽度

//文本对齐
//水平对齐
//垂直对齐
cxt.textAlign = "";
cxt.textBaseline = "";
```

#### 文本对齐

###### 水平对齐

|   值   |              描述              |
| :----: | :----------------------------: |
| start  |  默认。文本在指定的位置开始。  |
|  end   |     文本在指定的位置结束。     |
| center | 文本的中心被放置在指定的位置。 |
|  left  |          文本左对齐。          |
| right  |          文本右对齐。          |

![img](https://upload-images.jianshu.io/upload_images/665439-fd9bcc544a4cbf9e.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/850/format/webp)

###### 垂直对齐

|     值      |               描述               |
| :---------: | :------------------------------: |
| alphabetic  | 默认。文本基线是普通的字母基线。 |
|     top     |    文本基线是 em 方框的顶端。    |
|   hanging   |       文本基线是悬挂基线。       |
|   middle    |    文本基线是 em 方框的正中。    |
| ideographic |       文本基线是表意基线。       |
|   bottom    |    文本基线是 em 方框的底端。    |

![img](https://upload-images.jianshu.io/upload_images/665439-26617bb15bfe3aec.gif?imageMogr2/auto-orient/strip%7CimageView2/2/w/600/format/webp)

