jquery主要三个版本

兼容ie 6 7 8

1.x.x

不兼容ie 6 7 8 

2.x.x

3.x.x

jquery.cuishifeng.cn  //jQueryAPI网站

jQuery有两个全局变量，分别是jQuery和$

```javascript
<script src="https://cdn.bootcss.com/jquery/3.3.1/jquery.min.js"></script>
console.log(jQuery === $ );//true  jQuery与$是同一对象   都是对象数据类型 function
```

```html
<div id="wrap">
	<p></p>
	<p></p>
	<p></p>
</div>
<script src="https://cdn.bootcss.com/jquery/3.3.1/jquery.min.js"></script>
<script>
	console.log( $("#wrap p") === $("#wrap p") )//false
    $("#wrap p").html("123456");//给p标签里面添加123456   并且返回的值为$("#wrap p");
    $("#wrap p").css("color" , "red");//给p标签添加样式
    //可以简写成
    let $p = $("#wrap p");
    $p.html("123456");
    $p.css("color" , "red");
    //再或者
    $("#wrap p").html("123456").css("color" , "red")；
    $("w#rap p").eq(1)//获取第二个p标签
</script>
```

```html
<div id="wrap">
    <a></a>
	<p></p>
	<p class="goudan"></p>
	<p></p>
</div>
<script src="https://cdn.bootcss.com/jquery/3.3.1/jquery.min.js"></script>
<script>
	let $p = $("#wrap .goudan");
    console.log( $goudan.index() );//返回2 index里面默认获取在父级里面的序列号
    console.log( $goudan.index("#wrap p") );//返回1
</script>
```

```html
<div id="wrap">
	<p></p>
	<p></p>
	<p></p>
</div>
<script src="https://cdn.bootcss.com/jquery/3.3.1/jquery.min.js"></script>
<script>
	let $p = $("#wrap p");
    $p.each(function(i){
        //i是序列号
        console.log(this);//输出dom对象<p></p>
    })
</script>
```

