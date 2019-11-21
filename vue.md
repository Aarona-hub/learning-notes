# Vue.js

# 1. 单页面应用程序

> Single Page Application 
>
> 简称 SPA

### 1.1 网站交互方式

+ 经典的多页面

  > 例如 京东、唯品会

  + 前后端糅合在一起，开发和维护效率地下

  + 用户体验一般，点击刷新跳转，等待时间过长
  + 每个页面都需要重新加载渲染，速度慢
  + 有利于 SEO 搜索引擎搜索（蜘蛛会爬链接）

+ 现代式的单页面

  > 例如 网易云音乐、coding
  >
  > 单页面应用程序的最主要目的是为了让你的前后端开发能够分离，用户体验反而是其次的

  + 开发方式好，前后端分离，开发效率高，维护性好
    + 服务端不关心页面，只关心数据
    + 客户端不关心数据库及数据操作，只关心通过接口拿数据和服务端交互，处理页面

  + 用户体验好，就像一个原生的客户端软件一样使用
  + 只需要加载渲染局部视图即可，不需要整页刷新
  + 单页面应用开发技术复杂，所以诞生了一堆的开发框架
    + AngularJS
    + ReactJS
    + VueJS

  + 单页面技术其实已经很成熟了，但是都无法兼顾低版本浏览器
  + 但是现在除了一些电商网站，其实已经很少有系统需要兼容低版本浏览器
  + 大部分都是 ie9 以上
  + 单页面由于数据都是异步加载过来的，所以不会被搜索引擎搜索到，不利于 SEO 搜索
  + 手机 Web 网页
  + 管理系统

### 1.2 多页面：以服务端为主导，前后端混合

+ PHP案例，`.php`文件



### 1.3 单页面：前后端分离，各司其职

+ 服务端只处理数据
+ 前端只处理页面（两者通过接口交互）

### 1.4 模拟前后端分离开发模式

+ 项目立项
+ 需求分析
+ 服务端的工作
  + 需求分析
  + 设计数据库
  + 接口设计（有时候需要前端参与其中）
  + 接口（处理数据）开发
+ 前端的工作
  + 需求分析
  + 写页面
  + 页面写好写功能
  + 通过接口和服务端进行交互

#### 1.4.1 前后端分离： 多页

#### 1.4.2 前后端分离 ：单页



## 2.Vue.js 介绍

+ 作者：尤雨溪
+ Vue.js 是一套构建用户界面的`JavaScript`框架
+ 发展历史

### 2.1 MVVM







## Vue 面试题

### 一：如何理解 Vue 生命周期

### 二：如何进行非父子组件间的通信

### 三：Vue 的响应式原理

+ app.message 修改数据，Vue 内部是如何监听 message 数据的改变的
  + object.defineproperty => 监听对象属性的改变
+ 当数据发生改变，Vue 是如何知道要通知那些人，界面发生刷新
  + 发布订阅者模式

```javascript
<div id='app'> 
    {{message}} //张三
    {{message}} //李四  
	{{message}} //王五
 </div>
const obj = {
    message:'哈哈哈哈'，
    name：'zjg'
}
Object.keys(obj).forEach(key => {
    let value = obj[key]
    Object.defineProperty(obj,key,{
        set(newValue) {
            console.log('监听' + key + '改变')
            //告诉谁？谁用告诉谁？谁在用？
            //根据解析 html 代码，获取到谁再用属性
            value = newValue
        },
        get () {
            console.log('获取' + key + '对应的值' )
            // 张三：get() => update
            //lisi :get() => update
            //wangwu :get() => update
            return value
        }
    })
})
obj.name = 'kobe'

//发布者订阅模式
//发布者
class Dep {
    constructor () {
        this.subs = []
    }
    addSub (watcher) {
        this.subs.push(watcher)
    }
    notify () {
        this.subs.forEach(item => {
            item.update()
        })
    }
}
//订阅者
class Watcher {
    constructor (name){
        this.name = name
    }
    update () {
        console.log(this.name + '发生update')
    }
}
const dep = new Dep()
const w1 = new Watcher('zhangsan')
dep.addSub(w1)
const w2 = new Watcher('lisi')
dep.addSub(w2)
const w3 = new Watcher('wangwu')
dep.addSub(w3)

//调用 notify 通知三个人
dep.notify()

//最终打印
//张三发生update
//李四发生update
//王五发生update
```

+ 图解

  ![1570282203629](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570282203629.png)





