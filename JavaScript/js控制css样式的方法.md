改变css样式的方法之一：控制内部样式表（很少用）

```html
 <head>
 <style id="box"></style>
 </head>
 <body>
	<div id="wrap">
	</div>
	undefined<script type="text/javascript">
		var oCss = document.getElementById("box");
		oCss.innerHTML = " #wrap{width:100px;height:100px;background-color:#ccc;} ";
	</script>
 </body>
```

直接操作标签的属性

```html
<div style="" id="wrap" class="box" title="我是一个DIV"></div>
<script>
	var a = document.getElementById("wrap");
    	a.title = "我改变了div的title";
    	a.className = "wrap";
    	a.id = "b";
</script>
```

