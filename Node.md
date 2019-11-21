# Node  

## 1.Node.js是什么 

- Node.js® is a JavaScript runtime built on [Chrome's V8 JavaScript engine](https://v8.dev/).
  + Node.js不是一门语言
  + Node.js不是库、不是框架
  + Node.js是一个JavaScript运行是环境 
  + 简单点来讲，他可以解析和执行JavaScript
  + 也就是说现在的JavaScript可以完全脱离浏览器来运行
- 浏览器中的JavaScript
  + EcmaScript
    + 基本的语法
    + if
    + var
    + function
    + Object
    + Array
  + BOM
  + DOM
- Node.js中的JavaScript
  - 没有**BOM** 和**DOM**
  - Ecmascript
  - 在Node这个JavaScript执行环境中为JavaScript提供了一些服务器级别的操作API
    + 例如文件读写
    + 网络服务的构建
    + 网络通信
    + http服务器
    + 等处理
- Node.js uses an event-driven.non-blocking I/O modei that makes it lightweight and efficient
  - event-driven 事件驱动
  - non-blocking I/O modei 非阻塞I/O模型
  - lightweight and efficient 轻量和高效
- Node.js package ecosystem.npm is the largest ecosystem of   open source libraries in the world.
  - npm是世界上最大的开源库生态系统
  - 绝大多数JavaScript相关的包都存放在了npm上，这样做的目的是为了让开发人员更方便的去下载我并使用我

### 1.1Node.js能做什么 

- Web服务器后台
- 命令行工具
  + npm
  + git（C语言）
  + hexo（Node）
  + .....
- 对于前端工程师来说，接触node最多的是他的命令行工具
  - 自己写的很少
  - webpack
  - glup
  - npm

### 1.2.预备知识

- HTML
- CSS
- JavaScript
- 简单的命令行操作
  - cd
  - dir
  - ls
  - mkdir
  - rm
- 具有服务端开发经验更佳



### 1.3.一些资源

- 《深入浅出Node.js》
- 《Node.js权威指南》
  + API讲解
  + 也没有业务，没有实战
- JavaScript标准参考教程（alpha）：http://javascript.ruanyifeng.com/  
- Node入门 ：https://www.nodebeginner.org/
- 官方API文档：https://nodejs.org/en/
- 中文文档：http://nodeclass.com/api/node.html
- CNODE社区：https://cnodejs.org/
- CNODE入门：https://cnodejs.org/getstart

### 1.4. 这门课程你能学到啥

- B/S编程模型

  - Browser-Server
  - back-end
  - 任何服务端技术这种B/S编程模型都是一样的。和语言无关
  - Node只是作为我们学习BS编程模型的一个工具而已

- 模块化编程

  - RequireJs

  - SeaJs

  - ```javascript
    @import('文件路径')
    ```

  - 以前认知的JavaScript只能通过```script标签```来加载

  - 在Node中可以像```@import()```一样来引用加载JavaScript脚本文件

- Node常用API

- 异步编程

  - 回调函数
  - Promise
  - async
  - generator

- Express开发框架

- Ecmascript 6

  - 在课程中穿插讲解
  - 他只是一个新的语法而已

- ...

- 学习Node不仅会帮助大家打开服务端的盒子，同时会帮助你学习以后的前端高级内容

  - Vue.js
  - React
  - angular

## 2.起步

### 2.1.安装Node环境

- 查看当前Node环境版本号

- 下载:http://nodejs.org/en/download/

- 安装

  - 傻瓜式一路```next```就可以了
  - 对于已经安装过的，重新安装等于升级

- 确认Node环境是否安装成功

  + 打开命令行，输入```node --version```
  + 或者```node -v```

- 环境变量

  

### 2.2.Hello World

#### 2.2.1.解析执行JavaScript

1. 创建编写JavaScript脚本文件
2. 打开终端，定位脚本文件所属目录
3. 输入```node 文件名```执行对应的文件

注意：文件名不要使用```node.js```来命名，除了这个其他随便起，最后也不要用中文

- 解析执行JavaScript

- 读写文件

- http

  

## 3.Node中的JavaScript

- EcmaScript
  - 没有BOM.DOM
- 核心模块
- 第三方模块
- 用户自定义模块

### 3.1.EcmaScript

### 3.2.核心模块

Node为JavaScript提供了很多服务器级别的API，这些API绝大多数都被包装到了一个具名的核心模块中了。例如文件操作的```fs```核心模块，http服务构建的```http```模块，```path```路径操作模块，```os```操作系统信息模块......



以后只要我说这个模块是一个核心模块，你就要马上想到如果想要使用他，就必须

```javascript
1. var fs = require('fs')
2. var http = require('http')    
```

### 3.3.用户自定义模块

- require
- exports

### 3.4.第三方模块

## 4.Web服务器开发

### 4.1.ip地址和端口号

+  ip地址用来定位计算机
+  端口号用来定位具体的应用程序
+  一切需要联网通信的软件都会占用一个端口号
+  端口号的范围从0~65536之间
+  在计算机中有一些默认端口号，最好不要去使用
   + 例如http服务的80
+  我们在开发过程中使用一些简单好记的就可以了，例如3000、5000等没什么意义
+  可以同时开启多个服务，但一定要确保不同服务占用的端口号不一致才可以
+  也就是说，同一个端口号同一时间只能被一个程序占用

### 4.2.Content-Type

+ http://tool.oschina.net/

### 4.3. 请求对象Request

### 4.4.响应对象

### 4.5.在Node中使用模板引擎

#### 4.5.1.art-template

- art-template不仅可以在浏览器使用，也可以在node中使用

##### 安装

- npm install art-template
- 该命令在哪里执行就会把包下载到哪里。默认会下载到node_modules
- node_modules不要改，也不支持改

##### 在node中使用模板引擎

- 模板引擎最早就是诞生于服务器领域，后来才发展到前端

1. 安装 npm install art-template

2. 在需要使用的文件模块中加载 art-template

   只需要使用require方法加载就可以了：require（‘art-template’） 

   参数中的art-template就是你下载的包的名字

   也就是说你 install的名字是什么，则你require中的就是什么

3. 查文档，使用模板引擎的API

### 4.6. 统一处理静态资源

- 把当前模块所有的依赖项都声明在文件模块最上面
- 为了让目录结构保持统一清晰，所以我们约定，把所有的HTML文件都放在views（视图）目录中
- 我们为了方便的统一处理这些静态资源，所以我们约定把所有的静态资源都存放在public目录中，哪些资源能被访问，哪些资源不能被访问，我现在可以通过代码来进行非常灵活的控制

### 4.7.服务端渲染

+ 说白了就是在服务端使用模板引擎
+ 模板引擎最早诞生于服务端，后来才发展到了前端

### 4.8服务端渲染和客户端渲染的区别

+ 客户端渲染不利于SEO搜索引擎优化
+ 服务端渲染是可以爬虫抓取到的，客户端异步渲染是很那被爬虫抓取到的
+ 所以你会发现真正的网站既不是纯异步也不是纯服务端渲染出来的
+ 两者是结合来做的
+ 例如京东的商品列表就是采用服务端渲染，目的是为了SEO搜索引擎优化 
+ 而他的商品评论列表是为了用户体验，而且也不需要SEO优化，所采用是客户端渲染

## 5.留言本



## 6.Node中的模块系统

### 6.0. 使用Node编写应用程序主要就是在使用：

- EcmaScript语言
  - 和浏览器一样，在Node中没有BOM和DOM
- 核心模块
  - 文件操作的fs
  - http服务的http
  - url路径操作模块
  - path路径处理模块
  - os操作系统信息
- 第三方模块
  - art-template
  - 必须通过npm来下载才可以使用
- 咱们自己写的模块
  - 自己创建的文件

### 6.1.什么是模块化

- 文件作用域
- 通信规则
  - 加载require
  - 导出

### 6.2. CommonJS 模板规范

在Node中的javaScript还有一个很重要的概念：模块系统

- 模块作用域
- 使用require方法用来加载模块
- 使用exports接口对象用来导出模块中的成员

#### 6.2.1.加载 `require`

语法：

```javascript
var 自定义变量名称 = require（‘模块’）
```

两个作用：

- 执行被加载模块中的代码
- 得到被加载模块中的`exports`导出接口对象

#### 6.2.2.导出 `exports` 

- Node中是模块作用域，默认文件中所有的成员只在当天文件模块中有效
- 对于希望可以被其他模块访问的成员，我们就需要把这些公开的成员都挂载到`exports`接口对象中就可以了

导出多个成员{必须在对象中}

```javascript
exports.a = 123
exports.b = ‘hello’
exports.c = function(){
    console.log('ccc')
}
exports.d = {
    foo:'bar'
}
```



导出单个成员（拿到的就是：函数、字符串）

```javascript
module.exports = 'hello'
```

一下情况会覆盖：

```javascript
module.exports = 'hello'
//以这个为准，后者会覆盖前者
module.exports = function(x,y){
    return x = y
}
```

也可以这样来导出多个成员：

```javascript
module.exports = {
    add:function(){
        return x+y
    },
    str:'hello'
}
```

#### 6.2.3.原理解析

exports和`module.exports`的一个引用

```javascript
console.log(exports === module.exports) // =>true
exports.foo = 'bar'
//等价于
module.exports.foo = ‘bar’
```

#### 6.2.4.exports 和 module.exports 的区别

- exports 和 module.exports 的区别
  - 每个模块都有一个module对象
  - module对象中具有一个exports对象
  - 我么可以把需要导出的成员都挂载到`module.expots`接口对象中
  - 也就是： `module.exports.xxx = xxx`的方式
  - 但是每次都module.exports.xxx = xxx很麻烦，点儿的太多了
  - 所以Node为了你方便，同时在每一个模块中都提供了一个成员叫`expots`
  - `exports === module.exports`结果为true
  - 所以对于： `module.exports.xxx = xxx`的方式完全可以：`exports.xxx = xxx`
  - 当一个模块需要导出单个成员的时候，这个时候必须使用：`module.exports = xxx`的方式
  - 不要使用`exports.xxx`不管用
  - 因为每个模块最终向外导`return`的是`module.exports`
  - 而`exports`只是`module.exports`的一个引用
  - 所以即便你为`exports = xx`重新赋值，也不会影响`module.exports`
  - 但是有一种赋值方式比较特殊：`exports = module.exports`这个重新建立引用关系的
  - 之所以让大家明白这个道理，是希望可以更灵活的去使用它

#### 6.2.5.require方法加载规则

更多底层细节，自行参考：《深入浅出Node.js》中的模块系统章节

- 核心模块
  + 模块名
- 第三方模块
  - 模块名
- 用户自己写的
  + 路径



- 优先从缓存加载
- 判断模块标识
  * 核心模块
  * 第三方模块
  * 自己写的模块

```javascript
// 如果是非路径形式的模块标识
// 路径形式的模块：
//  ./ 当前目录，不可省略
//  ../ 上一级目录，不可省略
//  /xxx 几乎不用
//  d:/a/foo.js 几乎不用
//  首位的 / 在这里表示的是当前文件模块所属磁盘根路径
//  .js 后缀名可以省略
// require('./foo.js')

// 核心模块的本质也是文件
// 核心模块文件已经被编译到了二进制文件中了，我们只需要按照名字来加载就可以了
// require('fs')
// require('http')

// 第三方模块
// 凡是第三方模块都必须通过 npm 来下载
// 使用的时候就可以通过 require('包名') 的方式来进行加载才可以使用
// 不可能有任何一个第三方包和核心模块的名字是一样的
// 既不是核心模块、也不是路径形式的模块
//    先找到当前文件所处目录中的 node_modules 目录
//    node_modules/art-template
//    node_modules/art-template/package.json 文件
//    node_modules/art-template/package.json 文件中的 main 属性
//    main 属性中就记录了 art-template 的入口模块
//    然后加载使用这个第三方包
//    实际上最终加载的还是文件

//    如果 package.json 文件不存在或者 main 指定的入口模块是也没有
//    则 node 会自动找该目录下的 index.js
//    也就是说 index.js 会作为一个默认备选项
//    
//    如果以上所有任何一个条件都不成立，则会进入上一级目录中的 node_modules 目录查找
//    如果上一级还没有，则继续往上上一级查找
//    。。。
//    如果直到当前磁盘根目录还找不到，最后报错：
//      can not find module xxx
// var template = require('art-template')
// 
// 注意：我们一个项目有且只有一个 node_modules，放在项目根目录中，这样的话项目中所有的子目录中的代码都可以加载到第三方包
// 不会出现有多个 node_modules
// 模块查找机制
//    优先从缓存加载
//    核心模块
//    路径形式的文件模块
//    第三方模块
//      node_modules/art-template/
//      node_modules/art-template/package.json
//      node_modules/art-template/package.json main
//      index.js 备选项
//      进入上一级目录找 node_modules
//      按照这个规则依次往上找，直到磁盘根目录还找不到，最后报错：Can not find moudle xxx
//    一个项目有且仅有一个 node_modules 而且是存放到项目的根目录

```



### 6.3.npm

- node package manager

#### 6.3.1.npm网站

npmjs.com

#### 6.3.2.npm命令行工具

npm的第二层含义就是一个命令行工具，只要你安装node就已经安装了nom

npm也有版本的概念

可以通过在命令行中输入

```javascript
npm --version
```

升级npm（自己升级自己）

```javascript
npm install --global npm
```

#### 6.3.3常用命令

- npm init
  + npm init -y可以跳过向导，快速生成
- npm install
  + 一次性把dependencies选项中的依赖项全部安装
  + npm i
- nom install 包名
  + 只下载
  + npm i 包名
- npm install --save 包名
  + 下载并保存依赖项（package.json文件中的dependencies选项）
  + npm i -S 包名
- npm uninstall 包名
  + 只删除，如果有依赖项会依然保存
  + npm un 包名
- npm uninstall --save 包名
  + 删除的同时也会把依赖信息也去除
  + npm un -S 包名
- npm --help
  + 查看使用帮助
- npm 命令 --help
  + 查看指定命令的使用帮助
  + 例如我忘记了 uninstall命令的简写，这个时候，可以输入`npm uninstall --help`来查看使用帮助

#### 6.3.4.解决npm被墙问题

npm存储包文件的服务器在国外，有时候会被墙，速度很慢，所以我们需要解决这个问题

https://npm.taobao.org/淘宝的开发团队把npm在国内做了一个备份

安装淘宝的cnpm

```shell
#在任意目录下执行都可以
# --global 表示安装到全局，而非当前目录
# --global 不能省略，否则不管用
npm install --global cnpm
```





接下来你安装包的时候把之前的`npm`替换成`cnpm`

例如：

```javascript
//这里还是走国外的npm服务器，速度比较慢
npm install jquery

//使用cnpm就会通过淘宝的服务器来下载jquery
cnpm install jquery
```

如果不想安装`cnpm`又想使用淘宝的服务器来下载：

```shell
npm install jquery --registry=https://registry.npm.taobao.org
```

但是每次手动这样加参数很麻烦，所以我们可以吧这个选项加入配置文件中

```shell
npm config set registry http://registry.npm.taobao.org

#查看npm配置信息
npm config list
```

只要经过了上面命令的配置，则你以后所有的`npm install `都会默认通过淘宝的服务器来下载



### 6.4.package.json

我们建议每一个项目都要有一个`package.json`文件（包描述文件，就像产品的说明书一样），给人踏实的感觉

这个文件可以通过`npm init`的方式初始化出来

```javascript
C:\Users\Administrator.PC-20181127RBIS>npm init
This utility will walk you through creating a package.json file.
It only covers the most common items, and tries to guess sensible defaults.

See `npm help json` for definitive documentation on these fields
and exactly what they do.

Use `npm install <pkg>` afterwards to install a package and
save it as a dependency in the package.json file.

Press ^C at any time to quit.
package name: (administrator.pc-20181127rbis) npm-demo
version: (1.0.0)
description:
entry point: (.mongorc.js)
test command:
git repository:
keywords:
author:
license: (ISC)
About to write to C:\Users\Administrator.PC-20181127RBIS\package.json:

{
  "name": "npm-demo",
  "version": "1.0.0",
  "description": "",
  "main": ".mongorc.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC"
}


Is this OK? (yes)

```

对于咱们目前来讲，最有用的是`dependencies`选项，可以用来帮我们保存第三方包的依赖信息

如果你的`node_modules`删除了也不用担心，我们只需要：`npm install`就会自动把`package.json`中的`dependencies`中的所有依赖项都下载回来。

- 建议每个项目的根目录下都有一个`package.json`文件
- 建议执行`npm install 包名的`时候都加上`--save`这个选项，目的是用来保存依赖项信息

#### 6.4.1. package.json 和package-lock.json

npm 5 以前是不会有`package-lock.json`这个文件的

npm 5 以后才加入了这个文件

当你安装包的时候，npm都会生成或者更新`package-lock.json`这个文件

+ npm5以后的版本安装包不需要加`--save`参数，它会自动保存依赖信息
+ 当你安装包的时候，会自动创建或者是更新`package-lock.json`这个文件
+ `package-lock.json`这个文件会保存`node_modules`中所有包的信息（版本，下载地址）
  + 这样的话重新`npm install`的时候速度就可以提升
+ 从文件来看，有一个`lock`称之为锁
  + 这个`lock`是用来锁定版本的
  + 如果项目依赖了`1.1.1`版本
  + 如果你重新 install 其实会下载最新版本，而不是1.1.1
  + 我们的目的就是希望可以锁住1.1.1这个版本
  + 所以这个`package-lock.json`这个文件的另一个作用就是锁定版本号，防止自动升级新版

## 7. path 路径操作模块

参考文档 ：https://nodejs.org/dist/latest-v12.x/docs/api/path.html

+ path.basename
  + 获取一个路径的文件名(默认包含扩展名)
+ path.dirname
  + 获取一个路径中的目录部分
+ path.extname
  + 获取一个路径中的扩展名部分
+ path.parse
  + 把一个路径转为对象
    + root 根路径
    + dir 目录
    + base 包含后缀名的文件名
    + ext 后缀名
    + name 不包含后缀名的文件名
+ path.join
  + 当你需要进行路径拼接的时候，推荐使用这个方法
+ path.isAbsolute 判断一个路径是否是绝对路径

## 8.Node中的其他成员

在每个模块中，除了`require`、`exports`等模块相关API之外，还有两个特殊的成员

+ `_dirname` **动态获取** 可以用来获取当前文件模块所属目录的绝对路径
+ `_filename` **动态获取 **可以用来获取当前文件的绝对路径
+ `_dirname`和`_filename`是不受执行node命令所属路径影响的

在文件操作中，使用相对路径是不可靠的，因为在Node中文件操作的路径被设计为相对于执行 node 命令所处的路径(不是 bug ，人家这样设计是有使用场景的)。

所以为了解决这个问题，很简单，只需要把相对路径变为绝对路径就可以了。

那我们这里就可以使用`_dirname`和`_filename` 来帮我们解决这个问题了。

在拼接路径的过程中，为了避免手动拼接带来的一些低级错误，所以推荐多使用：`path.join`来辅助拼接。

所以为了尽量避免刚才所描述的这个问题，大家以后在文件操作中使用的相对路径都统一转换为**动态的绝对路径**

> 补充：模块中的路径标识和这里的路径没关系，不受影响(相对于文件模块)

## 9.Express

原生的http在某些方面表现不足以应对我们的开发需求，所有我们就需要使用框架来加快我们的开发效率。框架的目的就是提高效率，让我们的代码更高度统一。

在Node中，有很多Web开发框架，我们这里以学习`express`为主。

http://www.expressjs.com.cn/

### 9.1. 起步

#### 9.1.1 安装：

```shell
npm install --save express

```

#### 9.1.2. hello world

```shell
const express = require('express')
const app = express()

app.get('/', (req, res) => res.send('Hello World!'))

app.listen(3000, () => console.log('Example app listening on port 3000!'))

```

#### 9.1.3. 基本路由

路由器

+ 请求方法
+ 请求路径
+ 请求处理函数

get：

```javascript
//当你以 GET 方法请求 / 的时候，执行对应的处理函数
app.get('/', function (req, res) {
  res.send('Hello World!')
})

```

post:

```javascript
//当你以 POST 方法请求 / 的时候，执行对应的处理函数
app.post('/', function (req, res) {
  res.send('Got a POST request')
})

```

#### 9.1.4. 静态服务

```javascript
// /public资源
app.use(express.static('public'))

// /files资源
app.use(express.static('files'))

// /public/xxx
app.use('/public', express.static('public'))


// /static/xxx
app.use('/static', express.static('public'))


app.use('/static', express.static(path.join(__dirname, 'public')))

```

### 9.2.在Express中配置使用art-template模板引擎

- [art-template git-hub 仓库](https://aui.github.io/art-template/) 
- [art-template 官方文档](https://aui.github.io/art-template/) 

安装：

```shell
npm install --save art-template
npm install --save express-art-template

```

配置:

```javascript
// 第一个参数用来配置视图的后缀名，这里是 art ，则你存储在 views 目录中的模板文件必须是 xxx.art
//app.engine('art', require('express-art-template'));

//这里我把 art 改为 html
app.engine('html', require('express-art-template'));

```

使用:

```javascript
app.get('/',function(req,res){
    //express 默认会去项目中的views目录中找index.html
    res.render('index.html',{
        title:'hello world'
    })
})

```

如果希望修改默认的`views`视图渲染存储目录，可以：

```javascript
app.set('views',目录路径)   //注意第一个参数views千万不要写错

```

### 9.3. 在Express中获取表单 GET 请求参数

Express内置了一个API，可以直接通过`req.query`来获取

```shell
req.query

```



### 9.4. 在Express中获取表单 POST 请求体 数据

在Express中没有内置获取表单post请求体的API，这里我们需要使用一个第三方包：`bode-parser`.

安装：

```shell
npm install body-parser

```

配置：

```javascript
var express = require('express')
//0.引包
var bodyParser = require('body-parser')

var app = express()

//配置body-parser
//只要加入这个配置，则在req 请求对象上会多出来一个属性： body
//也就是说你就可以直接通过 req.body 来获取表单POST 请求体数据了
// parse application/x-www-form-urlencoded
app.use(bodyParser.urlencoded({ extended: false }))

// parse application/json
app.use(bodyParser.json())



```

使用：

```javascript
app.use(function (req, res) {
  res.setHeader('Content-Type', 'text/plain')
  res.write('you posted:\n')
    //可以通过 req.body来获取表单数据
  res.end(JSON.stringify(req.body, null, 2))
})

```

### 9.5.CRUD 

#### 9.5.0. 模块化思想

模块如何划分：

+ 模块职责要单一
+ Vue
+ angular
+ React
+ 也非常有利于学习前端三大框架

#### 9.5.1. 起步

- 初始化
- 安装依赖
- 模板处理

#### 9.5.2. 路由设计

| 请求方法 | 请求路径         | get参数 | post参数                       | 备注             |
| -------- | ---------------- | ------- | ------------------------------ | ---------------- |
| GET      | /students        |         |                                | 渲染首页         |
| GET      | /students/new    |         |                                | 渲染添加学生页面 |
| POST     | /students/new    | id      | name、age、gender、bobbides    | 处理添加学生请求 |
| GET      | /students/edit   |         |                                | 渲染编辑页面     |
| POST     | /students/edit   | id      | id、name、age、gender、hobbies | 处理编辑请求     |
| GET      | /students/delete |         |                                | 处理删除请求     |

#### 9.5.3. 提取路由模块

router.js

```javascript
/**
 * router.js 路由模块
 * 职责：
 *   处理路由
 *   根据不同的请求方法+请求路径设置具体的请求处理函数
 * 模块职责要单一，不要乱写
 * 我们划分模块的目的就是为了增强项目代码的可维护性
 * 提升开发效率
 */

var fs = require('fs')
var Student = require('./student')

// Express 提供了一种更好的方式
// 专门用来包装路由的
var express = require('express')

// 1. 创建一个路由容器
var router = express.Router()

// 2. 把路由都挂载到 router 路由容器中
router.get('/students',function(req,res){
    
})
router.get('/students/new',function(req,res){
    
})
router.post('/students/new',function(req,res){
    
})
router.get('/students/edit',function(req,res){
    
})
router.post('/students/edit',function(req,res){
    
})
router.get('/students/delete',function(req,res){
    
})
// 3. 把 router 导出
module.exports = router

```

app.js：

```javascript
var router= require('./router')

//挂载路由
app.use(router)

```

#### 9.5.4. 设计操作数据的API文件模块

```javascript
//student.js
//数据操作文件模块
//职责：操作文件中的数据，只处理数据，不关心业务


//获取所有学生列表
//return[]
exports.find() = function(){
    
}
//添加保存学生
exports.save() = function(){
    
}
//更新学生
exports.update() = function(){
    
}
//删除学生
exports.delete() = function(){
    
}

```

#### 9.5.5. 自己编写的步骤

- 处理模板
- 配置开放静态资源
- 简单路由：/students渲染静态页出来
- 路由设计
- 提取路由模块
- 由于接下来一系列的业务操作都需要处理文件数据，所以我们需要封装student.js。
- 先写好student.js文件结构
  + 查询所有学生列表的 API find
  + findByid
  + save
  + updateByid
  + deleteByid
- 实现具体功能
  + 通过路由收到请求
  + 接受请求中的数据（get、post）
    + req.query
    + req.body
  + 调用数据操作API处理数据
  + 根据操作结果给客户端发送响应
- 业务功能顺序
  + 列表
  + 添加
  + 编辑
  + 删除
- find
- findindex

### 9.6. 在Express 配置使用`express-session`插件

> 参考文档：https://github.com/expressjs/session

安装：

```shell
 npm install express-session

```

配置：

```javascript
// 该插件会为 req 请求对象添加一个成员 ： req.session 默认是一个对象
// 这是最简单的配置方式，暂且先不用关心里面参数的含义
app.use(session({
    //配置加密字符串，他会在原有加密基础之上和这个字符串拼起来去加密
    //目的是为了增加安全性，防止客户端恶意伪造
  secret: 'itcast',
  resave: false,
  saveUninitialized: false // 无论你是否使用 Session，我都默认直接给你分配一把钥匙
}))

```

使用：

```javascript
// 添加 Session 数据
req.session.foo = 'bar'

//获取 Session 数据
req.session.foo

```

提示：默认 Session 数据是内存存储的，服务器一旦重启就会丢失，真正的生产环境会把 Session 进行持久化存储。

## 10.MongoDB

参考 [教程](https://www.runoob.com/mongodb/mongodb-tutorial.html) 



### 10.1. 关系型数据库和非关系型数据库

表就是关系

或者说表与表之间存在关系。

+ 所有的关系型数据库都需要通过`sql`语言来操作
+ 所有的关系型数据库在操作之前都需要设计表结构
+ 而且数据表还支持约束
  + 唯一的
  + 主键
  + 默认值
  + 非空
+ 非关系型数据库非常的灵活
+ 有的非关系型数据库就是key-value 对儿
+ 但是MongoDB是长得最像关系型数据库的非关系型数据库
  + 数据库 -》数据库
  + 数据表 -》集合（数组）
  + 表记录-》文档对象
+ MongoDB不需要设计表结构
+ 也就是你可以任意的往里面存数据，没有结构性这么一说

### 10.2. 安装

+ http://www.mongodb.org
+ 下载
+ 安装
+ 配置环境变量
+ 最后输入`mongod --version`测试是否安装成功

### 10.3. 启动和关闭数据库

启动：

```shell
# mongodb 默认使用执行mongod命令所处盘符根目录下的/data/db作为自己的数据存储目录
# 所以在第一次执行该命令之前自己先手动新建一个 /data/db

mongod

```

如果想要修改默认的数据存储目录，可以：

```shell
mongod --dbpath= 数据存储目录路径

```

停止：

```shell
在开启服务的控制台，直接 Ctrl +c 即可停止

或者直接关闭开启服务的控制台也可以

```

### 10.4. 连接和退出数据库

连接：

```shell
#该命令默认连接本机的 MongoDB 服务
mongo

```

退出：

```shell
#在连接状态输入 exit 退出连接
exit

```

### 10.5. 基本命令

+ ```shell
  show dbs
  
  ```

  + 查看显示所有数据库

+ ```shel
  db
  
  ```

  + 查看当前操作的数据库

+ ```shell
  use 数据库名称
  
  ```

  + 切换到指定的数据（如果没有会新建）

+ 插入数据

### 10.6. 在Node中如何操作MongoDB数据库

#### 10.6.1. 使用官方的`mongodb`包来操作

+ 网址 ：https://github.com/mongodb/node-mongodb-native

#### 10.6.2. 使用第三方包`mongoose`来操作数据库

第三方包`mongoose`基于MongoDB官方的`mongodb`包做了一次封装

+ 网址 ：https://mongoosejs.com/

## 11. 异步编程

### 11.1. 回调函数

不成立的情况：

```javascript
function add(x,y) {
    console.log(1)
    setTimeout(function(){
        console.log(2)
        var ret = x + y
        return ret
    },1000)
    console.log(3)
    //到这里执行就结束了，不会等到前面的定时器，所以就直接返回了默认值 undefined
}
console.log(add(10,20) ==>undefined

```

不成立的情况：

```javascript
function add(x,y) {
    var ret
    console.log(1)
    setTimeout(function(){
        console.log(2)
        var ret = x + y
    },1000)
    console.log(3)
    return ret
}
console.log(add(10,20) ==>undefined

```

回调函数：

```javascript
function add(x,y,callback) {
    //callback 就是回调函数
    //var x = 10
    //var y = 20
    //var callback = function(ret) {console.log(ret)}
    console.log(1)
    setTimeout(function(){
        var rret = x + y
        callback(ret)
    },1000)
}

add(10,20,function(ret){
    //我现在拿到这个结果可以做任何操作
    console.log(ret)
})

```

基于原生 XMLHTTPRequest 封装 get 方法：

```javascript
function get(url, callback) {
      var oReq = new XMLHttpRequest()
      // 当请求加载成功之后要调用指定的函数
      oReq.onload = function () {
        // 我现在需要得到这里的 oReq.responseText
        callback(oReq.responseText)
      }
      oReq.open("get", url, true)
      oReq.send()
    }

    get('data.json', function (data) {
      console.log(data)
    })

```

### 11.2. Promise

参考文档：http://es6.ruanyifeng.com/

callback hell(回调地狱)：

![点击查看源网页](https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1565849002595&di=284cc72cf16efe258dc4a225bfc96c85&imgtype=0&src=http%3A%2F%2Faliyunzixunbucket.oss-cn-beijing.aliyuncs.com%2Fjpg%2F2451f1b01d709d237735a2b453c7b9aa.jpg%3Fx-oss-process%3Dimage%2Fresize%2Cp_100%2Fauto-orient%2C1%2Fquality%2Cq_90%2Fformat%2Cjpg%2Fwatermark%2Cimage_eXVuY2VzaGk%3D%2Ct_100)

无法保证顺序的代码：

```javascript
var fs = require('fs')

fs.readFile('./data/a.txt', 'utf8', function (err, data) {
  if (err) {
    // return console.log('读取失败')
    // 抛出异常
    //    1. 阻止程序的执行
    //    2. 把错误消息打印到控制台
    throw err
  } 
  console.log(data)
})    
  fs.readFile('./data/b.txt', 'utf8', function (err, data) {
    if (err) {
      // return console.log('读取失败')
      // 抛出异常
      //    1. 阻止程序的执行
      //    2. 把错误消息打印到控制台
      throw err
    }
    console.log(data)
   })
    fs.readFile('./data/c.txt', 'utf8', function (err, data) {
      if (err) {
        // return console.log('读取失败')
        // 抛出异常
        //    1. 阻止程序的执行
        //    2. 把错误消息打印到控制台
        throw err
      }
      console.log(data)
   
  
})


```

通过回调嵌套的方式来保证顺序：

```javascript
var fs = require('fs')

fs.readFile('./data/a.txt', 'utf8', function (err, data) {
  if (err) {
    // return console.log('读取失败')
    // 抛出异常
    //    1. 阻止程序的执行
    //    2. 把错误消息打印到控制台
    throw err
  }
  console.log(data)
  fs.readFile('./data/b.txt', 'utf8', function (err, data) {
    if (err) {
      // return console.log('读取失败')
      // 抛出异常
      //    1. 阻止程序的执行
      //    2. 把错误消息打印到控制台
      throw err
    }
    console.log(data)
    fs.readFile('./data/c.txt', 'utf8', function (err, data) {
      if (err) {
        // return console.log('读取失败')
        // 抛出异常
        //    1. 阻止程序的执行
        //    2. 把错误消息打印到控制台
        throw err
      }
      console.log(data)
    })
  })
})

```

为了解决以上代码方式带来的问题（回调地狱嵌套），所以在 EcmaScript 6 中新增了一个 API ：`promise`。

+ promise 的英文就是承诺、保证的意思（i promise u）

promise基本语法

```javascript
//1. 给别人一个承诺
//  Promise 容器一旦创建，就开始执行里面的代码
var p1 = new Promise(function(resolve,reject){
    //console.log(2)
    fs.readFile('./data/aa.txt','utf8',function(err,data){
        if (err) {
            //失败了，承诺容器中的任务失败了
            //console.log（err）
            //把容器中的 pending 状态变为 Rejected
            
            //调用 reject 就相当于调用了 then 的第二个参数传参
            reject(err)
        }else {
            //console,log(3)
            // 承诺容器中的任务成功了
            //console.log(data)
            //把容器中的 pending 状态改为成功 Resolved
            //也就是说这里调用的 resolve 方法实际上就是 then 方法传递的那个 function 
            resolve(data)
        }
    })
})
console.log(4)

//p1 就是那个承诺
//当 p1 成功了 然后(then)做指定的操作
// then 方法接受的 function 就是容器中的 resolve 函数
p1
  .then(function (data) {
    console.log(data)
}, function (err) {
    console.log('文件读取失败了' ， err)
})

```



封装promise版本的readFile：

```javascript
var fs = require('fs')

function pReadFile(filePath) {
  return new Promise(function (resolve, reject) {
    fs.readFile(filePath, 'utf8', function (err, data) {
      if (err) {
        reject(err)
      } else {
        resolve(data)
      }
    })
  })
}

pReadFile('./data/a.txt')
  .then(function (data) {
    console.log(data)
    return pReadFile('./data/b.txt')
  })
  .then(function (data) {
    console.log(data)
    return pReadFile('./data/c.txt')
  })
  .then(function (data) {
    console.log(data)
  })


```



### 11.3. Generator生成器函数

saync 函数

## 12.其他

### 12.1.代码风格

- airbnb JavaScript Style
  + 更专业规范
- JavaScript Standard Style
  + 符合大多数人的习惯

规范只是建议，可以遵守也可以不遵守，在一些比较专业的团队中，对于代码风格会有对应的风格校验工具，如果你的代码风格有问题，例如少了一个空格或者多了一个空格，你的代码都是不能提交的

后面会学习如何使用工具来强制校验代码风格问题。

#### 12.1.1. 代码无分号问题

无论你是否使用的是无分号的代码风格规范，都建议当一行代码是以：

+ `(`
+ `[`
+ ` 

以上三者开头的时候，最好都在其之前补一个分号。

例如：

```javascript
;(function(){
    
})()

```

#### 12.2. 修改完代码自动重启

我们这里可以使用一个第三方命名航工具：`nodemon`来帮助我们解决频繁修改代码重启服务器问题。

`nodemon`是一个基于Node.js开发的一个第三方命令行工具，我们使用的时候需要独立安装

```shell
#在任意目录执行该命令都可以
#也就是说，所有需要 --global 来安装的包都可以在任意目录中执行
npm install --global nodemon

```

安装完毕之后，使用：

```shell
node app.js

#使用nodemon
nodemon app.js

```

只要是通过`nodemon app.js`启动的服务，则它会监视你的文件变化，当文件发生变化的时候，自动帮你重新启动服务器.



#### 12.3. 文件操作路径和模块路径

文件操作路径：

```javascript
// 在文件操作的相对路径中
//    ./data/a.txt 相对于当前目录
//    data/a.txt   相对于当前目录
//    /data/a.txt  绝对路径，当前文件模块所处磁盘根目录
//    c:/xx/xx...  绝对路径
// fs.readFile('./data/a.txt', function (err, data) {
//   if (err) {
//     console.log(err)
//     return console.log('读取失败')
//   }
//   console.log(data.toString())
// })


```

模块操作路径：

```javascript
// 这里如果忽略了 . 则也是磁盘根目录
require('/data/foo.js')

//相对路径
require（'./data/foo.js'）

//模块加载的路径中的相对路径不能省略 ./

```

## 13.抽时间在讲的

### 12.1. 数组的reduce方法











