##### dependencies与devDependencies的区别

```shell
"dependencies是开发及运行环境是均需要的依赖  安装方式 npm install xxx -S 或者 npm install xxx --save"
"使用npm i xxx在npm5.0版本以上会被默认为开发及运行环境，即dependencies下面"
"devDependencies 只在开发是需要的依赖 安装方式 npm install xxx -D 或者 npm i xxx --save-dev"
"在我们按照包的时候需要尽可能的区分，因为可以减少node_modules目录的大小以及npm install花费的时间"
"构建工具（webpack、rollup...）、预处理器（less、stylus、sass...）、测试工具等等都是可以只安装到开发环境下的，即devDependencies"
```

##### webpack打包

```powershell
"单个文件打包"
"将a.js文章打包为b.js"
webpack a.js b.js
```



