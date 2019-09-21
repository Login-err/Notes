```html
<form action="demo.php" method="post/get">//action属性与type="submit"配合使用  action是把表单的数据传输到demo.php
    <button type="submit" formaction="demo.php">//formaction属性覆盖form的action属性
</form>                                                      
<button type="button/reset/submit" value="text name="btn">
<button type="button/reset/submit" value="text name="btn"></button>//button标签是定义一个按钮
//button:是可点击的按钮(ie默认值)  
//submit:该按钮是提交按钮(除IE外其他浏览器的默认值)                //reset：重置按钮(清空表单数据) 
```

```html
<input type="text name="input" value="submit">//value值即为按钮上显示的字  name在js中可通过document.getElementsByName("input");获取 
```

input框的type属性有button/checkbox/file/hidden/image/password/radio/reset/submit/text

![1542869259419](C:\Users\LENOVO\AppData\Roaming\Typora\typora-user-images\1542869259419.png)

