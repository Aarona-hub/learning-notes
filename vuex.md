# vuex

## 1. vuex 是做什么的

### 1.1官方解释

+ Vuex 是一个专为 Vue.js 应用程序开发的**状态管理模式**。

+ 它采用 集中式存储管理 应用的所有组件的状态，并以相应的规则保证状态以一种可预测的方式发生变化。

+ Vuex 也集成到 Vue 的官方调试工具 [devtools](https://github.com/vuejs/vue-devtools)[ extension](https://github.com/vuejs/vue-devtools)，提供了诸如零配置的 time-travel 调试、状态快照导入导出等高级调试功能。

### 1.2 **状态管理**到底是什么？

+ **状态管理模式、集中式存储管理**这些名词听起来就非常高大上，让人捉摸不透。

+ 其实，你可以简单的将其看成把需要多个组件共享的变量全部存储在一个对象里面。

+ 然后，将这个对象放在顶层的Vue实例中，让其他组件可以使用。

+ 那么，多个组件是不是就可以共享这个对象中的所有变量属性了呢？

### 1.3 等等，如果是这样的话，为什么官方还要专门出一个插件Vuex呢？难道我们不能自己封装一个对象来管理吗？

+ 当然可以，只是我们要先想想VueJS带给我们最大的便利是什么呢？没错，就是响应式。

+ 如果你自己封装实现一个对象能不能保证它里面所有的属性做到响应式呢？当然也可以，只是自己封装可能稍微麻烦一些。

+ 不用怀疑，Vuex就是为了提供这样一个在多个组件间共享状态的插件，用它就可以了。

## 2. 管理什么状态

+ 如果你做过大型开放，你一定遇到过多个状态，在多个界面间的共享问题。

+ 比如用户的登录状态、用户名称、头像、地理位置信息等等。

+ 比如商品的收藏、购物车中的物品等等。

+ 这些状态信息，我们都可以放在统一的地方，对它进行保存和管理，而且它们还是响应式的（待会儿我们就可以看到代码了，莫着急）。

## 3. 单界面的状态管理

![1570285032182](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570285032182.png)

### 3.1 图片中的三种东西怎么理解

+ state：不用多说，就是我们的状态
+ view：视图层，可以针对 State 的变化，显示不同的信息
+ Actions：这里的 Actions 主要是用户的各种操作：点击，输入等，会导致状态的改变

### 3.2 单界面状态管理的实现

![1570285267403](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570285267403.png)

+ 在这个案例中，counter 就是需要我们管理的状态
+ counter 需要某种方式被记录下来，也就是我们的State
+ counter 目前的值需要被显示在界面中，也就是我们的View 部分
+ 界面发生某些操作时(点击或者是 input)，需要去更新状态，也就是我们的 Actions

## 4. 多界面状态管理

+ Vue已经帮我们做好了单个界面的状态管理，但是如果是多个界面呢？

  + 多个视图都依赖同一个状态（一个状态改了，多个界面需要进行更新）
  + p不同界面的Actions都想修改同一个状态（Home.vue需要修改，Profile.vue也需要修改这个状态）

+ 也就是说对于某些状态(状态1/状态2/状态3)来说只属于我们某一个试图，但是也有一些状态(状态a/状态b/状态c)属于多个试图共同想要维护的

  + 状态1/状态2/状态3你放在自己的房间中，你自己管理自己用，没问题。

  + 但是状态a/状态b/状态c我们希望交给一个大管家来统一帮助我们管理！！！

    没错，Vuex就是为我们提供这个大管家的工具。

+ 全局单例模式（大管家）

  + p我们现在要做的就是将共享的状态抽取出来，交给我们的大管家，统一进行管理。
  + 之后，你们每个试图，按照我**规定好的**规定，进行访问和修改等操作。
  + 这就是Vuex背后的基本思想。

+ 图例

  ![1570286114373](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570286114373.png)

### 4.1 简单的案例

+ 首先我们需要在某个地方存放我们 vuex 的代码

  + 我们创建一个文件夹 store ，并在其中创建 index.js

  + 在 index 中写如下代码

    ![1570286447109](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570286447109.png)

+ 挂载到 Vue 实例中

  + 我们要让所有的 Vue 组件都可以使用这个 store 对象

    + 来到 main.js 文件，导入 store 对象，放在 new Vue 中

    + 然后就可以在其他组件，通过 this.$store 的方式，获取到这个对象

      ![1570286572634](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570286572634.png)

+ 使用 Vuex 的 count

  ![1570286619650](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570286619650.png)

### 4.2 小结

+ 1.提取出一个公共的store对象，用于保存在多个组件中共享的状态
+ 2.将store对象放置在new Vue对象中，这样可以保证在所有的组件中都可以使用到
+ 3.在其他组件中使用store对象中保存的状态即可
  + 通过this.$store.state.属性的方式来访问状态
  + 通过this.$store.commit('mutation中方法')来修改状态

> 注意：
>
> 我们通过提交mutation的方式，而非直接改变store.state.count
>
> 这是因为Vuex可以更明确的追踪状态的变化，所以不要直接改变store.state.count的值

## 5. Vuex 的核心概念

+ State
+ Getters
+ Mutation
+ Action
+ Module

### 5.1 State 单一状态树

+ Vuex提出使用单一状态树, 什么是单一状态树呢？
  + 英文名称是Single Source of Truth，也可以翻译成单一数据源。
+ 但是，它是什么呢？我们来看一个生活中的例子。
  + OK，我用一个生活中的例子做一个简单的类比。
  + 我们知道，在国内我们有很多的信息需要被记录，比如上学时的个人档案，工作后的社保记录，公积金记录，结婚后的婚姻信息，以及其他相关的户口、医疗、文凭、房产记录等等（还有很多信息）。
  + 这些信息被分散在很多地方进行管理，有一天你需要办某个业务时(比如入户某个城市)，你会发现你需要到各个对应的工作地点去打印、盖章各种资料信息，最后到一个地方提交证明你的信息无误。
  + 这种保存信息的方案，不仅仅低效，而且不方便管理，以及日后的维护也是一个庞大的工作(需要大量的各个部门的人力来维护，当然国家目前已经在完善我们的这个系统了)。

+ 这个和我们在应用开发中比较类似：
  + 如果你的状态信息是保存到多个Store对象中的，那么之后的管理和维护等等都会变得特别困难。
  + 所以Vuex也使用了单一状态树来管理应用层级的全部状态。
  + 单一状态树能够让我们最直接的方式找到某个状态的片段，而且在之后的维护和调试过程中，也可以非常方便的管理和维护。

### 5.2 Getters 基本使用

+ 有时候，我们需要从store中获取一些state变异后的状态，比如下面的Store中

  + 获取学生年龄大于20 的个数

    ![1570287262920](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570287262920.png)

  + 我们可以在 Store 中定义 getters

    + ![1570287300099](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570287300099.png)
    + ![1570287307246](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570287307246.png)

+ getters 作为参数和传递参数

  + 如果我们已经有了一个获取所有年龄大于20岁学生列表的getters, 那么代码可以这样来写

    ![1570287447262](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570287447262.png)

+ getters默认是不能传递参数的, 如果希望传递参数, 那么只能让getters本身返回另一个函数.

  + 比如上面的案例中,我们希望根据ID获取用户的信息

    ![1570287489561](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570287489561.png)

### 5.3 Mutation 状态更新

> 通常情况下，我们不在 mutation 中执行异步的操作

+ Vuex 的 store 状态的更新唯一方式:`提交 Mutation`
+ Mutation 主要包括两部分：
  + 字符串的事件类型
  + 一个回调函数，该回调的第一个参数就是 state
+ mutation 的定义方式
  + ![1570448577800](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570448577800.png)
+ 通过 mutation 更新
  + ![1570448610146](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570448610146.png)

### 5.4 Mutation 传递参数

+ 再通过 mutation 更新数据的时候，有可能我们希望携带一些额外的参数

  + 参数被称为 mutation 的载满（payload）

+ mutation 中的代码

  ![1570448740467](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570448740467.png)

+ 如果需要传递很多参数，我们通常会以对象的形式传递，也就是 payload 是一个对象，再从对象中提取出相关的信息

  ![1570448846346](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570448846346.png)

### 5.5 mutation 提交风格

+ 上面通过 commit 提交是一种普通的方式

+ vue 中还提供了另一种风格，它是包含 type 属性的对象

  ![1570448957531](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570448957531.png)

+ mutation 中的处理方式是将整个 commit 的对象作为 payload 使用，所以代码没有改变

  ![1570449014984](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570449014984.png)

### 5.6 mutation 的响应规则

+ Vuex 的 store 中的 state 是响应式的，当 state 中的数据发生改变时，Vue 组件会自动更新
+ 这就要求我们必须遵守一些 Vue 对应的规则
  + 提前在 store 中初始化好一些需要的属性
  + 当给 state 中的对象添加新属性时，使用下面的方式
    + 一：使用 Vue.set（obj，'newProp,123'）
    + 二：用新对象给旧对象重新赋值
+ 例子：
  + 下面的方式一和方式二都可以让 state 中的属性是响应式的
  + ![1570449292249](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570449292249.png)

### 5.7 mutation 常量类型

+ 在 mutation 中我们定义了很多事件类型（也就是其中的方法名称），当项目增大时，方法也会越来越多，如何解决这个问题呢？
+ 我们可以创建一个文件，mutation-type.js 并且在其中定义我们的常量

+ 常量类型代码
+ ![1570449490400](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570449490400.png)
+ ![1570449499971](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570449499971.png)
+ ![1570449504855](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570449504855.png)

### 5.8 Action 的基本定义

> Action 类似于 Mutation，但是是用来代替 mutation 来进行异步操作的

#### 5.8.1 基本代码

![1570449722982](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570449722982.png)

+ 在 Vue 组件中，如果我们需要调用 action 中的方法，那么就需要使用 dispatch
+ ![1570449795749](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570449795749.png)

+ 同样也支持传递 payload
+ ![1570449832146](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570449832146.png)

#### 5.8.2 Action 返回的 Promise

+ Promise 经常用于异步操作
+ 代码如下：
+ ![1570449897745](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570449897745.png)

+ 

![1570449914406](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570449914406.png)

### 5.9 认识 Module

+ Vue 使用单一状态树，那么也就意味着很多状态都会交给Vuex来管理
+ 当应用非常复杂时，store 对象就有可能变得相当臃肿
+ 为了解决这个问题，Vuex 允许我们将 store 分割成块（module）,而每个模块拥有自己的 state mutations actions getters
+ 代码如下
  + ![1570450124798](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570450124798.png)

#### 5.9.1 Module 局部状态

+ 上面的代码中，我们已经有了整体的组织结构，下面我们来看看具体的局部模块中的代码如何书写
  + 我们在 moduleA 添加state、mutations、getters
  + mutation 和 getters 接受的第一个参数是局部状态对象
+ ![1570450451242](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570450451242.png)

+ ![1570450457925](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570450457925.png)

> 注意：虽然，我们的 doubleCount 和 increment 都是定义在对象内部的，但是在调用的时候，依然是通过 this.$store 来直接调用的

#### 5.9.2 Actions 的写法

+ acions 的写法：接受一个 context 参数对象
  + 局部状态通过 context.state暴露出来，根节点状态则为 context.rootState
  + ![1570450699367](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570450699367.png)

+ 如果 getters中也需要使用全局的状态，可以接受更多的参数
  + ![1570450734180](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570450734180.png)

### 6.0 项目结构

+ 当我们的 Vuex 帮助我们管理过多的内容时，好的项目结构可以让我们的代码更加清晰
+ ![1570450807232](C:\Users\Administrator.PC-20181127RBIS\AppData\Roaming\Typora\typora-user-images\1570450807232.png)

