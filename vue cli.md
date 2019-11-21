#  Vue CLI

> CLI 是 Command-line interface，翻译为命令行界面，俗称脚手架
>
> 官方发布
>
> 使用 vue-cli 可以快速搭建 Vue 开发环境以及对应的 webpack 配置

## 1. 使用前提

+ 全局安装 webpack ` npm install wbpack -g`

## 2. 使用

### 2.1 安装

+ npm i  -g @vue/cli
+ Vue cli2 初始化项目：`vue init webpack 项目名`
+ Vue cli3 初始化项目:`vue create 项目名`

## 3. Vue CLI2

![1570283147650](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570283147650.png)

+ 目录结构详解

  ![1570283184406](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570283184406.png)

+ Runtime-Compiler和Runtime-only的区别

  + ![1570283289577](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570283289577.png)
  + 简单总结
    + 如果在之后的开发中，你依然使用template，就需要选择Runtime-Compiler
    + 如果你之后的开发中，使用的是.vue文件夹开发，那么可以选择Runtime-only

+ Runtime-Compiler 和 Runtime-only

  ![1570283444743](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570283444743.png)

![1570283451641](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570283451641.png)

+ vue 程序运行过程

  ![1570283482137](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570283482137.png)

+ render 函数的使用

  ![1570283533028](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570283533028.png)

![1570283539038](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570283539038.png)

![1570283544965](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570283544965.png)

+ npm run build

  ![1570283592962](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570283592962.png)

+ npm run dev

  ![1570283611532](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570283611532.png)

+ 修改配置：webpack.base.cong.js 起别名

  ![1570283678749](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570283678749.png)

## 4.Vue CLI3

### 4.1 vue cli2 和 vue cli3 的区别

+ vue-cli 3 是基于 webpack 4 打造，vue-cli 2 还是 webapck 3

+ vue-cli 3 的设计原则是“0配置”，移除的配置文件根目录下的，build和config等目录

+ vue-cli 3 提供了 vue ui 命令，提供了可视化配置，更加人性化

+ 移除了static文件夹，新增了public文件夹，并且index.html移动到public中

> ![1570283832678](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570283832678.png)

+ 目录结构详解

  ![1570283853630](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570283853630.png)

+ 自定义配置：起别名

  ![1570283883109](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570283883109.png)

