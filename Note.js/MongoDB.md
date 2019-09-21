+ 下载
+ 配置环境变量   D:\MongoDB\mongodb-win32-x86_64-2008plus-ssl-3.6.11\bin



```cmd
https://www.mongodb.com/download-center/community  MongoDB //下载网址
mongod --dbpath '拖拽文件夹的路径' //运行mongodb
改端口
mongod --dbpath '拖拽文件夹的路径' --port '端口号'
```

##### mongodb常用指令

``show dbs``列出所有的数据库名字

``use '数据库名'``使用admin数据库 若改数据库名不存在 它会自动创建

MongoDB数据库组成

* 集合 集合是由文档组成  很多集合组成了一个数据库
* 文档

``use student``创建student数据库，此时输入``db.jihe1``这里的db指的是student数据库，jihe1是student下面的一个集合，没有这个集合的话也会自动创建，在该集合中插入数据``db.jihe1.insert({name:'huanglian',sex:'男',age:18})``

mododb的常用函数

* 向数据库集合中插入一个文档
* db.collection.insert('文档');// 文档是json格式
* db.collection.find();// 查找数据
* db.collection.updata();// 更改数据
* db.collection.remove();// 删除数据

