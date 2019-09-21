```javascript
/*
	Linux复制粘贴Ctrl+c与Ctrl+v 而是Ctrl+ins（复制）与shift+ins（粘贴）
*/
/*
	首先在Linux里面安装npm
		yum install npm -y
    检测npm是否安装成功
    	npm -v（centOS的yum安装的npm是3.10.10的版本，比较低，但是不影响后面几步的操作，当完成node安装之后，自动升级npm）
	通过npm安装n模块（n模块的作用是node的版本管理器）
		npm i n -g
    检测n模块是否安装成功（会显示很大一段n的命令）
    	n --help
    通过n命令来安装和切换各个版本的node
    	安装 n stable 安装稳定版本
    		n latest 安装最新版本
    		n x.x.x  安装x.x.x版本的node
    	切换
    		直接按n回车，上下方向键选择当前需要的node版本
    	（安装或切换后，需要关闭xshell，才能通过node -v 检测到当前版本的node，npm版本也会自动升级）
    在服务器运行node项目
    	把项目在本地测试好
    	把项目文件通过ftp上传到服务器，注意不要上传node_modules 因为内容太多很慢，可以在服务器用npm i命令安装依赖
    	在xshell运行nodejs文件启动服务
    	使用公网ip：端口的形式，所有人都可以访问你的程序 
        vim 文件名 进入文件 
        	按i进行编辑
        	先按esc退出然后在：wq保存退出
*/
/*
	进程守护 pm2
		安装（根目录安装 cd /）
			npm i pm2 -s
		检测是否安装成功
			pm2 -v
		运行程序
			pm2 start 文件名.js
		停止服务
			pm2 stop 文件名.js
		程序运行状态
			pm2 list
*/

/*
	配置环境变量
		添加软链接
			ln -s 路径 /usr/local/bin/名称
			例如pm2
             ln -s /usr/local/src/node-v6.11.1-linux-x64/bin/pm2 /usr/local/bin/pm2 
*/

/*
	安装MongoDB
	创建一个文件 
		vim /etc/yum.repos.d/mongodb-org-4.2.repo
	把文档里面的内容粘贴进去
	[mongodb-org-4.2] 
    name = MongoDB Repository 
    baseurl = https://repo.mongodb.org/yum/redhat/$releasever/mongodb-org/4.2/x86_64/ 
    gpgcheck = 1 
    enabled = 1 
    gpgkey = https：// www.mongodb.org/static/pgp/server-4.2.asc
    然后保存
    
    运行命令
    sudo yum install -y mongodb-org
    
    完成
    
    mongod -f /etc/mongod.conf 启动命令
*/
```

