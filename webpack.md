# webpack

> 从本质上来讲，webpack 是一个现代的 JavaScript 应用的静态模块打包工具。

## 1.webpack 的安装

+ 安装 webpack 首先需要安装 node.js，node.js 自带了软件包管理工具 npm

+ 全局安装 webpack

  ```shell
  npm install webpack -g
  ```

+ 局部安装 webpack

```shell
cd 对应目录
npm install webpack --save-dev

#--save-dev 是开发时的依赖，项目打包后不需要继续使用的
```

+ 为什么全局安装后，还需要局部安装？
  + 在终端执行 webpack 命令，使用的是全局安装的 webpack
  + 当在 package.json 中定义了 scripts 时，其中包含了 webpack 命令，那么使用的是局部的 webpack

## 2.打包

### 2.1.创建文件夹和文件

+ dist 文件夹：用于存放之后打包的文件
+ src 文件夹：用于存放我们写的源文件
+ index.html：浏览器打开展示的首页
+ package.json：通过 `npm init -y`生成，npm 包管理的文件
+ mathUtils.js
+ main.js

### 2.2. js 文件打包

```shell
webpack src/main.js dist/bundle.js
```

+ 打包后会在 dist 文件下生成一个 bundle.js 文件，我们只需要将这个 js 文件在 index.html 中引入即可

### 2.3. 入口和出口

+ 如果每次使用 webpack 的命令都需要写上入口和出口作为参数，非常麻烦。

  + 解决办法：创建一个 webpack.config.js 文件

  ```shell
  module.exports = {
    entry:'./src/main.js',
    output:{
      path:path.resolve(__dirname,'../dist'),
      filename:'bundle.js',
      // publicPath:'dist/'
    },
    }
  ```

### 2.4. 局部安装 webpack

+ 目前，我们使用的 webpack 是全局的，如果我们想使用局部来打包？
  + 因为一个项目往往依赖特定的 webpack 版本，全局的可能和这个项目的版本不一致，导致打包出现问题
  + 所以通常一个项目，都有自己局部的 webpack。
+ 安装

```shell
 npm i webpack --save-dev
```

+ 第二步，通过 node_modules/.bin/webpack 启动 webpack 打包

```shell
node_modules/.bin/webpack
```

+ 在 package.json 中定义启动
  + package.json 中的 scripts 的脚本在执行时，会按照一定的顺序寻找命令对应的位置
    + 首先，会寻找本地的 node_modules/.bin 路径中对应的命令
    + 如果没找到会去全局的环境变量中寻找
  + ![1568204611726](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1568204611726.png)
  + 如何执行我们的 build 指令呢？
  + ![1568204623537](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1568204623537.png)

## 3. webpack 中的 loader

> loader 是 webpack 中的一个非常核心的概念

+ webpack 用来做什么呢？
  + 在我们之前的实例中，我们主要是用来处理我们写的 js 代码，并且它会自动处理 js 之间相关的依赖
  + 但是，在开发中，我们也需要加载 css、图片、也包括一些高级的将 ES6 转成 ES5 代码，less 转成 css，将 jsx、.vue 文件转成 js 文件等等
  + 所以此时就需要给 webpack 扩展对应的 loader 就行了
+ loader 使用过程
  + 一：通过 npm 安装需要使用的 loader
  + 二：在 webpack.config.js 中的 modules 关键字下面进行配置
+ 大部分 loader 我们都可以在 webpack 的官网找到，并且学习用法

### 3.1.CSS 文件处理

+ 安装 css-loader 和 style-loader

```shell
npm i css-loader style-loader --save-dev
```

+ 按照下图配置

#### ![1568205313735](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1568205313735.png)

> 注意：style-loader 需要放在 css-loader 的前面
>
> 因为 webpack 在读取使用 loader 的时候，是按照从右向左的顺序读取的

### 3.2. less 文件处理

+ 如果我们希望在项目中使用 less、sass、stylus 来写样式

+ 安装 less 和 less-loader

```shell
npm i less-loader less --save-dev
```

+ 其次，修改对应的配置文件
+ ![1568205728233](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1568205728233.png)

### 3.3. 图片文件处理

+ 安装 url-loader

```shell
npm i url-loader --save-dev
```

+ 修改 webpack.config.js 配置文件：
+ ![1568205867161](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1568205867161.png)

+ 运行后，图片是通过 base64 显示出来的
+ 这是 limit 属性的作用，当图片小于 8kb 时，对图片就行 base64 编码
+ 如果大于 8kb 时，我们需要安装 file-loader

```shell
npm i file-loader -save-dev
```

+ 再次打包，就会发现 dist 文件夹下多了一个图片文件

![1568206107942](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1568206107942.png)

+ 这是 webpack 自动帮助我们生成的一个非常长的名字，是一个 32 位 hash 值，目的是为了防止名字重复，但是开发中我们对名字是有要求的，比如，将所有的图片放在一个文件夹中，跟上原来图片的名称，同时防止重复
+ 所以我们在 options 中添加上如下选项
  + img：文件要打包的文件夹
  + name：获取图片原来的名字，放在该位置
  + hash8：依然使用 hash，但是保留八位
  + ext：使用图片原来的扩展名

![1568206396838](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1568206396838.png)

+ 此时，图片不会显示，因为路径不正确，我们需要在路径下添加一个 dist/

  ![1568206835202](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1568206835202.png)

### 3.4. ES6 语法处理

> webpack 打包的 js 文件 并没有将语法转换为 ES5 ，会导致不支持 ES6 的浏览器没办法运行代码

+ 我们希望将语法转换，此时就需要使用 babel
  + 安装：npm i babel-loader@7 babel-core babel-preset-es2015
+ 配置 webpack.config.js 文件

![1568207048355](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1568207048355.png)

+ 重新打包便可

## 4. 引入 vue.js

安装：npm i vue --save

+ 接下来就可以使用 vue 开发了

![1568207191786](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1568207191786.png)

+ 修改完成重新打包，没有出现效果，打包过程中没有错误
+ 在浏览器有报错

![1568207305093](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1568207305093.png)

+ 这个错误说的是我们使用的是nruntime-only版本的Vue，什么意思呢？
  + 这里我只说解决方案：[Vue](http://cn.vuejs.org/v2/guide/installation.html)[不同版本构建](http://cn.vuejs.org/v2/guide/installation.html)，后续我具体讲解runtime-only和runtime-compiler的区别
  + 修改 webpack 的配置，添加如下内容
  + ![1568207390845](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1568207390845.png)

### 4.1 el 和 template 的区别

+ 正常运行之后，我们来考虑另外一个问题：
  + 如果我们希望将data中的数据显示在界面中，就必须是修改index.html
  + 如果我们后面自定义了组件，也必须修改index.html来使用组件
  + 但是html模板在之后的开发中，我并不希望手动的来频繁修改，是否可以做到呢？

+ 定义template属性：
  + 在前面的Vue实例中，我们定义了el属性，用于和index.html中的#app进行绑定，让Vue实例之后可以管理它其中的内容
  + 这里，我们可以将div元素中的{{message}}内容删掉，只保留一个基本的id为div的元素
  + 但是如果我依然希望在其中显示{{message}}的内容，应该怎么处理呢？
  + 我们可以再定义一个template属性，代码如下：

![1568207593855](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1568207593855.png)

+ 重新打包，运行程序，显示一样的结果和HTML代码结
+ 那么，el和template模板的关系是什么呢？
  + 在我们之前的学习中，我们知道el用于指定Vue要管理的DOM，可以帮助解析其中的指令、事件监听等等。
  + 而如果Vue实例中同时指定了template，那么template模板的内容会替换掉挂载的对应el的模板。

+ 这样做有什么好处呢？
  + 这样做之后我们就不需要在以后的开发中再次操作index.html，只需要在template中写入对应的标签即可
  + 但是，书写template模块非常麻烦怎么办呢？
  + 没有关系，稍后我们会将template模板中的内容进行抽离。
  + 会分成三部分书写：template、script、style，结构变得非常清晰。

### 4.2. vue组件开发引入

+ 在学习组件化开发的时候，我说过以后的Vue开发过程中，我们都会采用组件化开发的思想
+ ![1568207878310](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1568207878310.png)

### 4.3. .vue 文件封装处理

![1568208040783](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1568208040783.png)

+ 安装 vue-loader 和 vue-template-compiler

  ```shell
  npm install vue-loader vue-template-compiler --save-dev
  
  ```

+ 修改 webpack.config.js 的配置文件

+ ![1568208029930](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1568208029930.png)

## 5.plugin

+ plugin 和 loader 的区别
  + plugin是插件，它是对webpack本身的扩展，是一个扩展器
  + loader主要用于转换某些类型的模块，它是一个转换器。
+ plugin 使用过程
  + 一：通过npm安装需要使用的plugins(某些webpack已经内置的插件不需要安装)
  + 二：在webpack.config.js中的plugins中配置插件。

#### 5.1. 添加版权的 plugin

> 该插件名字叫BannerPlugin，属于webpack自带的插件。

+ 按照下面的方式修改 webpack.config.js 文件
+ ![1568208286152](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1568208286152.png)

+ 重新打包，查看 bundle 的头部：
+ 

![1568208316329](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1568208316329.png)

#### 5.2. 打包 html 的plugin

+ 目前，我们的index.html文件是存放在项目的根目录下的。
  + 我们知道，在真实发布项目时，发布的是dist文件夹中的内容，但是dist文件夹中如果没有index.html文件，那么打包的js等文件也就没有意义了。
  + 所以，我们需要将index.html文件打包到dist文件夹中，这个时候就可以使用`HtmlWebpackPlugin`插件

+ HtmlWebpackPlugin插件可以为我们做这些事情：
  + 自动生成一个index.html文件(可以指定模板来生成)
  + 将打包的js文件，自动通过script标签插入到body中

+ 安装：`npm install html-webpack-plugin
  --save-dev`

+ 使用插件，修改 webpack.config.js 文件中 plugins 部分的内容 如下：
  + ![1568208495591](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1568208495591.png)

#### 5.3. js 压缩的 plugin

+ 在项目发布之前，我们必然需要对js等文件进行压缩处
  + 这里，我们就对打包的js文件进行压缩
  + 我们使用一个第三方的插件uglifyjs-webpack-plugin，并且版本号指定1.1.1，和CLI2保持一致

+ 安装：`npm install
  uglifyjs-webpack-plugin@1.1.1 --save-dev`

+ 修改 webpack.config.js 文件，使用插件：
  + ![1568208633693](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1568208633693.png)

+ 打包过后的 bundle.js 就是已经被压缩过的

### 6. 搭建本地服务器

+ webpack提供了一个可选的本地开发服务器，这个本地服务器基于node.js搭建，内部使用express框架，可以实现我们想要的让浏览器自动刷新显示我们修改后的结果。
+ 不过它是一个单独的模块，在webpack中使用之前需要先安装它
+ 安装：`npm install --save-dev
  webpack-dev-server@2.9.1`
+ devserver也是作为webpack中的一个选项，选项本身可以设置如下属性：
  + contentBase：为哪一个文件夹提供本地服务，默认是根文件夹，我们这里要填写./dist
  + port：端口号
  + inline：页面实时刷新
  + historyApiFallback：在SPA页面中，依赖HTML5的history模式

+ webpack.config.js 文件配置如下：
+ ![1568208790336](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1568208790336.png)

+ 我们还可以在配置另外一个 scripts：
  + --open 参数表示直接打开浏览器
