#### node.js操作mongoose

下载mongoose``npm install mongoose --save``

```javascript
// mongoose这个模块可以在node.exe环境中操作
const mongoose = require('mongoose');
// 27017下面的端口
mongoose.connect('mongodb://localhost:27017/student',{useNewUrlParser:true},(err)=>{
    if(err){
        console.log('数据库连接失败');
       return 
    }
    console.log('数据库连接成功')
})
// {useNewUrlParser:true} 去除警告
```

###### 定义数据库中的数据格式（写在回调函数位置）

```javascript
let studentScheme = new mongoose.Schema({
    name:String,
    sex:String,
    age:Number
})
// 向banji这个集合中添加文档  这里的集合会自动添加s 此处的班级会变成banjis  s的结尾的不会  比如s还是s集合
let Student = mongoose.model('banji',studentScheme);
let xiaoming = new Student({
    name:'xiaoming',
    sex:'男',
    age:18
});
// 往数据库中插入数据
xiaoming.save();

// 查找
Student.findOne({name:'xiaoming'},(err,result)=>{console.log(err,result)})
Student.findOne(name:'xiaoming').then((result)=>{console.log(result)})

// 删除一个
Student.deleteOne({name:'xiaoming'},(err,result)=>{
    console.log(err,result);
});
// 删除多个
Student.deleteMany({name:'xiaoming'},(err,result)=>{
    console.log(err,result);
});

// 修改
Student.updateOne({name;'xiaoming'},{$set:{name:'huanglian'}},(err,result)=>{
    console.log(err,result)
})

Student.findById('id',(err,result)=>{
    console.log(err,result)
})
```

###### post请求

```javascript
const express = require('express')
const app = express();
const bodyParser = require('body-parser')
//post请求使用
//中间件只解析urlencoded 请求体，并返回，只支持UTF-8编号文本，支持gzip deflate 压缩。
//extended ture->使用queryString库（默认） false->使用qs库。
app.use(bodyParser.urlencoded({
    entended:false
}))
//中间件只会解析 json ，允许请求提任意Unicode编码支持 gzip 和 deflate 编码。
app.use(bodyParser.json())

app.get('/path',(req,res)=>{
    req.query;//get请求才能用req.query
})
app.post('/path',(req,res)=>{
    req.body
})
```

##### mongoose里面的关联表

```javascript
const mongoose = require('mongoose');
const db = mongoose.connect('mongodb://localhost');
const Schema = mongoose.Schema
const StudentSchema  = Schema({
    name:String,
    xuexiao:{
        type:Schema.Types.ObjectId,
        ref:"schools"//数据库名称
    }
})
const SchoolSchema = Schema({
    name:String
})

const model1 = mongoose.model('students',StudentSchema)
const model2 = mongoose.model('schools',SchoolSchema)


const student1 = model({
    name:'huanglian',
    xuexiao:'58ddd5db6216a905ce973de4'//是学校数据库的一个id
}).save()
const student2 = model({
    name:'huanglian111',
    xuexiao:schools_id
}).save()


model1.find({name:'huanglian'}).exec((err,result)=>{console.log('id: ', student.xuexiao, 'name: ', student.xuexiao.name);
 //id:  58ddd5db6216a905ce973de4 name:  undefined
//这里打印只有id，并没有属性
})

model1.find({name:'huanglian111'}).populate('xuexiao').exec((err,result)=>{console.log('id: ', student.xuexiao, 'name: ', student.xuexiao.name);
//   id:  { _id: 58ddd5db6216a905ce973de4, 
//         name: '第一高中',
//          __v: 0 } 
// name:  第一高中
})

/*我们不加populate，查询出来的是为_id，然后我们根据这个_id去查询相应的表，就可以得到相应的结果，这也就是连表的本质*/
```

```javascript
//获取数据库集合里面的总数
const Article = require('schema/article');
Article.countDocuments().then((counts)=>{
    console.log(counts);//获取数据库集合里面的总数
})
/*
	skip：从第几条开始
	limit：限制返回的条数
	sort：按照id升序还是降序排列
*/
Article.find().populate('tag').limit(count).skip(page*count).sort({'_id':-1}).then((result)=>{
    res.send({data:result,totalCounts,maxPages})
})
```

