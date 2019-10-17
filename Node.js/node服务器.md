##### node搭建服务器

每次更改node.js都需要重新打开node.js  因此在本地测试可以输入命令行``npm i nodemon -g``安装nodemon，每次使用时把node输入改成nodemon，如果是在真实服务器的话，可以安装``npm i pm2 -g``安装

```
const http = require('http');
http.createServer(function(req,res){
//200是状态码
    res.writeHeader(200,{
        //解决跨域问题
        'Access-Control-Allow-Origin':'*',
        //防止乱码
        'Content-Type':'text/plain;charset=utf8'
    })
    res.end('恭喜你成功请求到了服务器')
}).listen(7001);//端口号
```

