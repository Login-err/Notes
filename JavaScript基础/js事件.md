```javascript
onmouseenter//鼠标移入事件
onmouseleave//鼠标移出事件
ondblclick//鼠标双击事件
onfocus//聚焦事件
onblur//失焦事件
```

```html
<input type="text">
<scippt>
	var inp = document.getElementsByTagName("input")[0];
    inp.onchange = function(){};//input框值改变，然后还得标签失去焦点
    inp.oninput = function(){};//input框值发生改变
</scippt>
```

