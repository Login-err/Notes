

##### 本地账号

```
git config --global user.name "你的用户名"
git config --global user.email "你的邮箱"
git config --list // 查看是否绑定好
```

```
~ //家目录
huanglian$ // 普通用户
cd 文件夹名 // 进入文件夹
ls // 当前目录所有文件
mkdir 文件夹名 // 创建文件夹
ctrl+l // 清屏
touch test.txt// 新建text.txt文件
open text.txt// 打开text.txt
vim// 编辑
先按esc 然后输入  :wq// 保持并退出
上箭头// 重复上一条命令
// 工作区来声明要提交的文件  还未提交到git仓库
git add //  全都提交
git add test.txt // 提交部分文件
// 提交到版本库
git commit -m "" // 引号里面是提交的描述
```

##### 初始化仓库

使用``git init``

###### 添加到git仓库

1.使用``git add <filepath>``,可反复多次使用，添加多个文件

2.使用``git commit``,提交到版本库，完成

##### 查看提交状态

+ 如果要随时掌握工作区状态，使用``git status``命令

+ 如何``git status``告诉你有文件被修改，用``git diff``可以查看到修改的内容

##### 版本回退

``git log``可以看到每一个版本的信息

``(HEAD -> master)``相当于最近版本信息的指针

``git reflog``精简版的``git log``

``git reset --hard "id值"``id值在git reflog里面可以看见或者返回前一次``git reset --hard HEAD^``  如果是前前次``git reset --hard HEAD^^`` 

