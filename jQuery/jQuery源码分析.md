##### jQuery的整体结构

```javascript
(function (window,undefined){
    var jQuery =  function(){
        return new jQuery.prototype.init();
    }
    jQuery.prototype = {
        constructor: jQuery
    }
    jQuery.prototype.init.prototype = jQuery.prototype;
})(window)
```

##### jQuery的入口函数

```javascript
/*
	1.当传入 '' null undefined NaN 0 false ，返回空的jQuery对象
	2.字符串：
		代码片段：会将创建好的Dom元素存储到jQuery对象中返回
		选择器：会将找到的所有元素存储到jQuery对象中返回
	3.数组
		会将数组中存储的元素依次存储到jQuery对象中返回
	1.除上述类型之外
		会将传入的数据存储到jQuery对象中返回
*/
```

##### jQuery入口函数写法

```javascript
(function (window,undefined){
    var jQuery =  function(){
        return new jQuery.prototype.init();
    }
    jQuery.prototype = {
        constructor: jQuery,
     	init:function(selector){
            // 去除首尾空格
            selector = jQuery.trim(selector);
            // 传入为NaN 0 false undefined null ""
            if(!selector){
                return this;
            } else if(jQuery.isString(selector)){
            // 传入为字符串
                if(jQuery.isHTML(selector)){
                    var temp = document.createElement('div');
                    temp.innerHTML = selector;
                    
                    {
                        for(var i = 0,len = temp.children.length;i<len;i++){
                            this[i] = temp.children[i];
                        }
                        this.length = temp.children.length;
                    }
                    
                    {[].push.apply(this, temp.children);}
                    // 花括号内效果一样
                    return this;
                } else {
                    var res = document.querySelectorAll('selector');
                    [].push.apply(this,res);
                    return this;
                }
            } else if(
            // 传入为数组
                typeof selector === "object"
                && "length" in selector
                && selector !== window
            ){
                {
                    // 判断是不是真数组
                    if(({}).toString.apply(selector) === "[object Array]"){
                        // 将数组转化为伪数组
                        [].push.apply(this, selector);
                        return this;
                    } else { // 伪数组
                        // 将自定义数组转化为伪数组
                        var arr = [].slice.call(selector);
                        // 将数组转化为伪数组
                        [].push.apply(this,arr);
                    }
                }
                // 上下花括号可代替
                {
                    
                        // 将自定义数组转化为伪数组
                        var arr = [].slice.call(selector);
                        // 将数组转化为伪数组
                        [].push.apply(this,arr);
                }
                return this;
            } else {
                // 除上述以外
                this[0] = selector;
                this.length = 1;
                return this;
            }
        }   
    }
    
    // 判断是不是字符串
    jQuery.isString = function(str){
        return typeof str === "string";
    }
    
    // 判断是不是HTML代码片段
    jQuery.isHTML = function(str){
        return 
        str.charAt(0) == "<"
        && str.charAt(str.length - 1) == ">"
        && str.length >= 3;
    }
    
    // 去除首尾空格
    jQuery.trim = function(str){
        if(!jQuery.isString){
            return
        }
        if(str.trim){
            return str.trim();
        } else {
          	return str.replace(/^\s+|\s+$/g,"");  
        }
    }
    
    // 判读是不是对象
    jQuery.isObject = function(elem){
        return typeof elem === "object";
    }
    
    // 判断是不是window
    jQuery.isWindow = function(elem){
        return elem === window;
    }
    
    // 判断是不是数组
    jQuery.isArray = function(elem){
        if(
            jQuery.isObject(elem)
        	&& !jQuery.isWindow(elem)
            && "length" in elem
        ){
            return true;
        } else {
            return false;
        }
    }
    
    // 判断是不是函数
    jQuery.isFunction = function(elem){
        return typeof elem === "function"
    }
    jQuery.prototype.init.prototype = jQuery.prototype;
})(window)
```

##### 优化上面代码

```javascript
(function (window,undefined){
    var jQuery =  function(){
        return new jQuery.prototype.init();
    }
    jQuery.prototype = {
        constructor: jQuery,
     	init:function(selector){
            // 去除首尾空格
            selector = jQuery.trim(selector);
            // 传入为NaN 0 false undefined null ""
            if(!selector){
                return this;
            } else if(jQuery.isString(selector)){
            // 传入为字符串
                if(jQuery.isHTML(selector)){
                    var temp = document.createElement('div');
                    temp.innerHTML = selector;
                    
                    {
                        for(var i = 0,len = temp.children.length;i<len;i++){
                            this[i] = temp.children[i];
                        }
                        this.length = temp.children.length;
                    }
                    
                    {[].push.apply(this, temp.children);}
                    // 花括号内效果一样
                    return this;
                } else {
                    var res = document.querySelectorAll('selector');
                    [].push.apply(this,res);
                    return this;
                }
            } else if(
            // 传入为数组
                typeof selector === "object"
                && "length" in selector
                && selector !== window
            ){
                {
                    // 判断是不是真数组
                    if(({}).toString.apply(selector) === "[object Array]"){
                        // 将数组转化为伪数组
                        [].push.apply(this, selector);
                        return this;
                    } else { // 伪数组
                        // 将自定义数组转化为伪数组
                        var arr = [].slice.call(selector);
                        // 将数组转化为伪数组
                        [].push.apply(this,arr);
                    }
                }
                // 上下花括号可代替
                {
                    
                        // 将自定义数组转化为伪数组
                        var arr = [].slice.call(selector);
                        // 将数组转化为伪数组
                        [].push.apply(this,arr);
                }
                return this;
            } else {
                // 除上述以外
                this[0] = selector;
                this.length = 1;
                return this;
            },
            extend:function(obj){
                for(var key in obj){
                    this[key] = obj[key];
                }
            } 
        }   
    }
    
    // 判断是不是字符串
    jQuery.extend({
        
    })
    isString : function(str){
        return typeof str === "string";
    },
    
    // 判断是不是HTML代码片段
    isHTML : function(str){
        return 
        str.charAt(0) == "<"
        && str.charAt(str.length - 1) == ">"
        && str.length >= 3;
    },
    
    // 去除首尾空格
    trim : function(str){
        if(!jQuery.isString){
            return
        }
        if(str.trim){
            return str.trim();
        } else {
          	return str.replace(/^\s+|\s+$/g,"");  
        }
    },
    
    // 判读是不是对象
    isObject : function(elem){
        return typeof elem === "object";
    },
    
    // 判断是不是window
    isWindow : function(elem){
        return elem === window;
    },
    
    // 判断是不是数组
    isArray : function(elem){
        if(
            jQuery.isObject(elem)
        	&& !jQuery.isWindow(elem)
            && "length" in elem
        ){
            return true;
        } else {
            return false;
        }
    },
    
    // 判断是不是函数
    isFunction : function(elem){
        return typeof elem === "function"
    }
    jQuery.prototype.init.prototype = jQuery.prototype;
})(window)
```

