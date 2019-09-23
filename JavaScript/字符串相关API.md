##### 对象相关的API

```html
classList.add();
classList.remove();
classList.toggle()
<div class="goudan dachui" id="box"></div>
<script>
	var a = document.getElementById("box")
	a.classList.add("hl");//div的class变成goudan，dachui，hl,若一样则
	a.classList.remove("dachui");//div的class变成goudan
    a.classList.toggle("show");//div中有show的话删除，没有的话增加
</script>
```

```html
onchange()
<div id="box"></div>
<script>
	var oBox = document.getElementById("box");
    oBox.onchange = function(){
        ...
    }
</script>
```

