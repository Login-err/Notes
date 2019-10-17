```javascript
//node是什么
/*
	node是构建在Chrome V8 引擎上的一个JavaScript运行环境
*/
// node跟Chrome有什么区别
/*
	架构一样，都是基于事件驱动的异步架构
	
	浏览器主要通过事件驱动来服务页面交互

	node主要是通过事件驱动来服务 I/O
	node 没有HTML,Webkit和显卡等等的UI技术支持
*/
// node es + 模块
```

##### Buffer

```javascript
/*
	二进制文件
		.mp3
		.mp4
		.png
		......
	Buffer是一种数据结构
		里面专门存放二进制数据的，为了方便显示，以十六进制数据显示
		buf.length 表示字节长度
			一个英文单词的字节长度是1
			一个中文汉字的字节长度是3
		字符串转成buffer数据 							Buffer.from(str);
		Buffer转成字符串
			buf1.toString();
*/
let str = 'heaven';
// 生成buffer数据
let buf1 = Buffer.from(str);
console.log(buf1);// 生成buffer数据结构
buf1.toString();// 转换成字符串
// Buffer.alloc(指定字节长度)  其中不会含有未清理的数据
let buf2 = Buffer.alloc(10);// 指定生成10个字节的内存空间
// Buffer.allocUnsafe(指定字节长度)   但其中会含有内存中没有清理的数据
let buf3 = Buffer.allocUnsafe(10);
```

##### fs

```javascript
/*
	fs模块是node.js 中内置的一个核心模块
		file system  这个模块专门用来对系统文件的增删改查各种操作
*/
const fs = require('fs');
// fs的方法都含有一个同步与异步  加了sync的是同步
//fs.writeFile(文件路径，写入的数据，options,回调函数)  路径相对于根目录 可绝对路径也可相对路径
** fs.writeFile('./hello.txt','hello node',(err)=>{
    if(err){
        console.log(err);
    }else{
		console.log('数据写入成功')
    }
});// 异步方法
fs.writeFileSync('./huanglian.txt','hello world')
// writeFile 可以在文件里面写入任何数据类型，所有的数据都会被隐式转换为字符串
console.log('我是同步代码');
// 先执行同步代码  err也可以换成其他的，第一个一定是err(也可以是其他字母表示)
// 异步才有回调函数
fs.writeFile('./hello.txt','hello node',{flag:'a'},(err)=>{
    if(err){
        console.log(err);
    }else{
		console.log('数据写入成功')
    }
});
// flag默认为w，即覆盖之前的   a为追加之前的


/*fs.readFile(路径,{编码},回调函数);
	1.读到的数据为buffer
*/
** fs.readFile('./helle.txt',(err,data)=>{
    if(err){
        console.log(err);
    }else{
        console.log(data.toString());
    }
})
// 如何没有toString则会二进制数据


//删除文件
//fs.unlink(路径,回调函数); 
fs.unlinkSync('./hello.txt')

//  删除文件夹
// fs.rmdir(路径,回调函数);
// remove directory
fs.rmdir();

// 新建一个文件夹
fs.mkdir('',callback);

// 读文件夹
** fs.readdir('',callback);

// 限制文件里面的字节
fs.truncateSync('url',10);// 限制字节长度

// 判断指定路径下的文件/文件夹存不存在  文件有后缀名 文件夹没有后缀名
let result = fs.existSync('./hello');// 该方法的异步已移除

// 文件相关信息
let result = fs.stat('./hello.txt');
// 文件大小获取
console.log(result.size)


// 对文件夹重命名 对文件进行移动
// fs.rename(旧路径,新路径,回调函数)
// 		1.首先把旧路径移动到新路径
//		2.并且进行改名
** fs.rename('./Buffer.js','01.js',(err)=>{
    if(err){
    console.log(err)
	}                                      });// 把Buffer.js换成01.js


// fs.watchFile('url',{interval:10,callback}) interval是设置时间间隔
fs.watchFile('./hello.txt',(cur,prev=>{
    console.log(cur.size);//  cur是当前文件里面的状态，cur.size是获取文件字节数大小
    console.log(prev.size);//  prev是上一次变化前的文件状态
})
```

```javascript
const fs = require(fs);
fs.readFile('url',(err,data)=>{
    if(err){
        console.log(err);
    }else{
        console.log(data);
    }
})
// fs的局限性读取小文件比较方便，读取大的文件不方便

const rs = fs.createReadStream('url');
// 对于当前文件创建一个可读流   可读流的默认状态是静止的
rs.resume();// 让可读流中的数据发生流动 改变可读流的状态 
// 也可以用下面这个方法改变可读流的状态
rs.on('data',(chunk)=>{
    // 绑定data事件 也可以让可读流的数据运动
    console.log(chunk);
    ws.write(chunk);// 复制数据  或者fs.pipe(ws)
})
fs.pipe(ws);// 只使用了一根管子 直接读取复制
rs.on('end',()=>{
    console.log('数据读取完成了···')
});// 对rs绑定一个结束事件

// 可写流
const ws = fs.createWriteStream('url');// url是写入的地址的文件名
ws.write(chunck);
```

##### 模块引入

```javascript
/*
	模块的分类：
		核心模块 fs path
		自定义模块
			必须使用路径得 ./  ../
			每个模块默认都是相互独立的
			如果想要a模块想要给b模块的数据
			必须让b模块自己使用exports暴露自己的数据
		第三方模块
*/

/*
	每个模块中的代码都是包裹在一个立即执行的函数中，类似于(function(){}()),同时立即执行函数中都有五个形参
    exports		专门用来暴露模块数据的一个对象，实质是通过module.exports暴露，如果exports = {a:2}  这种方法不行  但是如果通过 module.exports = {a:2}  这种可行
    require		专门用来引入外部模块的函数
    module		当前模块的对象
    _filename	当前文件的绝对路径
    _dirname	当前文件夹路径
*/

// 1.js
let a = 2;
let b = 3;
exports.heaven = a
// 2.js
let first = require('./1.js');// 对于自定义模块必须写./  不然会报错
console.log(a);// 会报错，a is not define
console.log(first.heaven); // 是在添加了exports.heaven之后才不会报错
// 1.js得暴露变量a  1.js里面写 exports.heaven = a
```

##### path模块

```javascript
// 引入path模块  专门操作路径
const path = require('path');
let result = path.parse(_dirname);
path.parse(url);// 获取一个对象
path.parse(_filename);
path.basename(_filename);// 获取文件名
path.extname(_filename);// 获取后缀名
path.dirname(_filename);// 获取路径
path.join(_dirname,'abc');// 合并出一个新的路径  结果变成 变成  原url/abc
```

##### http模块

```javascript
// 引用http模块 这是node的一个核心模块
const http = require('http');
// 创建一个服务
/*
	request是客服端向服务器发送的请求
	response是服务器向客户端发回的响应  
	res.write('hello world'); 在页面显示hello world
	res.write('<h1>我是首页</h1>')  但是编码格式有问题 如果解决该问题则在它前面添加 res.setHeader('content-type','text/html;charset=utf-8')
	res.end()  结束本次服务
*/
let server = http.createServer((req,res)=>{
    console.log(req.method);// 请求方式 比如get/post
    console.log(req.url);// 端口号后面部分，不包括hash值
    res.end();
})
// 监听端口
server.listen(3000);// 3000是端口号
```

##### url模块

```javascript
// node的核心模块 专门用来处理地址栏的字符串
const url = require('url');
let str = 'https://www.baidu.com:8080/p/a/t/h?user=huanglian&age=20#1';
url.parse(str);// 得到url相关信息
```

```javascript
const fs = require('fs');
const url = require('url');
const http = require('http');
let server = http.createServer((req,res)=>{
    let {pathname,query} = url.parse(req.url,true);
    if(pathname === '/index.html'){
        fs.readFile('.'+pathname,(err,data)=>		{
            if(err){
                res.end('no such file')
            }else{
                res.end(data);
            }
        })
    }else if(pathname === '/css/css01.css'){
        fs.readFile('.'+pathname,(err,data)=>		{
            if(err){
                res.end('no such file')
            }else{
                res.end(data);
            }
        })
    }else if(pathname === '/images/01.png'){
        fs.readFile('.'+pathname,(err,data)=>		{
            if(err){
                res.end('no such file')
            }else{
                res.end(data);
            }
        })
    }
})
```

```javascript
const url = require('url');
const fs = require('fs');
const http = require('http');
let server = http.createServer(err,(req,res)=>{
    if(err){
        console.log(err)
    }else{
        // post 数据是存放在buffer中的，需要使用querystring模块来获取
        let str = '';
        req.on('data',(chunk)=>{
            str += chunk;
        })
        req.on('end',()=>{
            let post  = qs.parse(str);
            console.log(post);// 返回form提交的数据转换后的对象
            res.end('OK');
        })
    }
})
```



##### qs

```javascript
// 查询字符串
const qs = require('querystring');
let str = 'xinming:'huanglian',province:'hunan',sex：‘human’'
qs.parse(str);
console.log(str);// {xinming:'huanglian',province:'hunan',sex：‘human’}
```

