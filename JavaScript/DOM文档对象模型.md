```html
<div id="wrap">
    <p></p>
    <a href="#"></a>
</div>
<script>
    let oWrap = document.getElementById("wrap");
    let text = document.createTextNode("hhhh");//创建文本节点
    oWrap.appendChild(oText);//在oWrap里面添加文本节点
    let ele = document.createElement("div");//创建元素节点
    oWrap.appendChild(ele);//在oWrap里面添加div元素
    let oA = document.getElementsByTagName("a")[0];
    oWrap.insertBefore(ele,oA);//在a标签前面添加div元素
</script>
```

