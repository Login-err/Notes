#### vue-cli中跨域解决方案

```javascript
/*
* 在config/index.js里面的proxyTable文件中设置跨域 
* 调用的时候比如要请求'http://www.abc.com/aa/aaa'只需请求/api/aa/aaa即可
*/
 proxyTable: {
    '/api': {//此处的/api不可以改
          target: 'http://www.abc.com',  //目标接口域名
          changeOrigin: true,  //是否跨域
          pathRewrite: {
            '^/api': '/api'   //重写接口（没有api可以不写）
      }
}
```

###### 当请求图片时出现403forbidden的时候，在index.html里面加上

```html
<meta name="referrer" content="no-referrer" />
```

