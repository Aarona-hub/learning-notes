## mongoose

+ 官网：https://mongoosejs.com/
+ 官方指南：https://mongoosejs.com/docs/guide.html
+ 官方API文档：https://mongoosejs.com/docs/api.html

## 1.MongoDB 数据库的基本概念

+ 可以有数据库
+ 一个数据库中可以有多个集合（表）
+ 一个集合中可以有多个文档（表记录）
+ 文档结构很灵活，没有任何限制
+ MongoDB非常灵活，不需要像MySQL 一样先创建数据库，表，设计表结构
  + 在这里只需要，当你需要插入数据的时候，只需要指定往哪个数据库的哪个集合操作就可以了
  + 一切都由MongoDB来帮你自动完成建库建表这件事儿

```javascript
{
    qq：{
       users:[
           {name:'张三'，age:15},
           {name:'张四'，age:15},
           {name:'张五'，age:15},
           {name:'张六'，age:15},
           {name:'张七'，age:15}
       ] ,
       products:[
           
          
       ]
    },
    taobao:{
         
     },
    baidu:{
         
     }
}
```



## 2. 起步

安装：

```shell
npm i mongoose
```

hello world：

```javascript
const mongoose = require('mongoose');
mongoose.connect('mongodb://localhost:27017/test', {useNewUrlParser: true});

const Cat = mongoose.model('Cat', { name: String });

const kitty = new Cat({ name: 'Zildjian' });
kitty.save().then(() => console.log('meow'));
```

## 3.官方指南

### 3.1. 设计 Scheme 发布 Model 

```javascript
var mongoose = require('mongoose')

var Schema = mongoose.Schema

// 1. 连接数据库
// 指定连接的数据库不需要存在，当你插入第一条数据之后就会自动被创建出来
mongoose.connect('mongodb://localhost/itcast')

// 2. 设计文档结构（表结构）
// 字段名称就是表结构中的属性名称
// 约束的目的是为了保证数据的完整性，不要有脏数据
var userSchema = new Schema({
  username: {
    type: String,
    required: true // 必须有
  },
  password: {
    type: String,
    required: true
  },
  email: {
    type: String
  }
})

// 3. 将文档结构发布为模型
//    mongoose.model 方法就是用来将一个架构发布为 model
//    第一个参数：传入一个大写名词单数字符串用来表示你的数据库名称
//                 mongoose 会自动将大写名词的字符串生成 小写复数 的集合名称
//                 例如这里的 User 最终会变为 users 集合名称
//    第二个参数：架构 Schema
//   
//    返回值：模型构造函数
var User = mongoose.model('User', userSchema)


// 4. 当我们有了模型构造函数之后，就可以使用这个构造函数对 users 集合中的数据为所欲为了（增删改查）
```

### 3.2. 增加数据

```javascript
var admin = new User({
  username: 'zs',
  password: '123456',
  email: 'admin@admin.com'
})

admin.save(function (err, ret) {
  if (err) {
    console.log('保存失败')
  } else {
    console.log('保存成功')
    console.log(ret)
  }
})
```

### 3.3. 查询数据

查询所有：

```javascript
User.find(function (err, ret) {
  if (err) {
    console.log('查询失败')
  } else {
    console.log(ret)
  }
})

```

按条件查询：

```javascript
User.find({
  username: 'zs'
}, function (err, ret) {
  if (err) {
    console.log('查询失败')
  } else {
    console.log(ret)
  }
})
```

按条件查询单个：

```javascript
User.findOne({
  username: 'zs'
}, function (err, ret) {
  if (err) {
    console.log('查询失败')
  } else {
    console.log(ret)
  }
})
```

### 3.4. 删除数据

根据数据删除所有：

```javascript
User.remove({
  username: 'zs'
}, function (err, ret) {
  if (err) {
    console.log('删除失败')
  } else {
    console.log('删除成功')
    console.log(ret)
  }
})
```

根据条件删除一个：

```java
Model.findOneAndRemove(conditions,[options],[callback])
```

根据id删除一个：

```javascript
Model.findByIdAndRemove(id,[options],[callback])
```



### 3.5. 更新数据

根据条件更新所有：

```javascript
Model.update(conditions,doc,[options],[callback])
```

根据指定条件更新一个：

```javascript
Model.findOneAndUpdate([conditions],[update],[options],[callback])
```

根据id更新一个：

```javascript
User.findByIdAndUpdate('5a001b23d219eb00c8581184', {
  password: '123'
}, function (err, ret) {
  if (err) {
    console.log('更新失败')
  } else {
    console.log('更新成功')
  }
})
```

