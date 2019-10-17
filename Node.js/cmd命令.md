跳转到指定目录

``cd+'路径'``

返回上一级

``cd+../``

在指定目录创建一个文件夹

``md + '文件夹名'``

在指定目录下删除一个文件夹

``rd+'文件夹名'``

在指定目录创建一个文件

``cd.>hello.txt//在该文件下创建一个hello.txt``

删除一个文件夹

``del hello.txt``

开发环境  项目上线之前的环境  devD...

生产环境 项目上线之后的环境  dependencies

npm 全称是 node package manager node的包管理器

npm 的常用指令   在npm中下载的所有包都会放在node_moudles中

安装一个包：npm install '包名' --save

卸载一个包：npm uninstall '包名' 

-- save  是在生产环境中使用

-- save-dev  在开发环境中使用



npm init 初始化一个描述文件

npm install 这条指令会自动安装package.json文件中的dependencies的devDependencies		