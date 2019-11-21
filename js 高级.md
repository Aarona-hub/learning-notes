# javaScript 基础总结

## 1. 数据类型说明

### 1.1 分类

+ 基本（值）类型：
  + Number:任意数值
  + String:任意文本
  + Boolean：true/false
  + undefined：undefined
  + null：null
+ 对象（引用）类型：
  + Object：任意对象
  + Array：特别的对象类型（下标/内部数据有序）

### 1.2 判断

+ typeof：
  + 可以区别：数值，字符串，布尔值，undefined，function
  + 不能区别：null与对象，一般对象与数组
+ instanceof：
  + 专门用来判断对象数据的类型：Object，Array与function
+ ===：
  + 可以判断 undefined 和 null

### 1.3 undefined 与 null

+ 区别：

  + undefined 代表没有赋值
  + null 代表赋值了，只是值为 null

+ 什么时候给变量赋值为 null ？

  ```javascript
  var a = null    //a 将指向一个对象，但对象此时还没有确定
  a = null      // 让 a 指向的对象成为垃圾对象
  ```

### 1.4 严格区别变量类型与数据类型

+ js的变量本身是没有类型的，变量的类型实际上是变量内存中数据的类型
+ 变量类型
  + 基本类型：保存基本类型数据的变量
  + 引用类型：保存对象地址值的变量
+ 数据对象
  + 基本类型
  + 对象类型

### 1.5 什么是数据？

+ 存储与内存中代表特定信息的'东东'，本质就是0101二进制
+ 具有可读和可传递的基本特性
+ 万物（一切）皆数据，函数也是数据
+ 程序中所有操作的目标：数据
  + 算数运算
  + 逻辑运算
  + 赋值
  + 调用函数传参

### 1.6 什么是内存

+ 内存条通电后产生的存储空间（临时的）
+ 产生和死亡：内存条(集成电路板)==>通电==>产生一定容量的存储空间==>存储各种数据==>断电==>内存全部消失
+ 内存的空间是临时的, 而硬盘的空间是持久的
+ 一块内存包含两个数据
  + 内部存储的数据（一般数据/地址数据）
  + 内存地址值数据
+ 内存分类
  + 栈：全局变量, 局部变量 (空间较小)
  + 堆：对象 (空间较大)

### 1.7 什么是变量

+ 值可以变化的量, 由变量名与变量值组成
+ 一个变量对应一块小内存, 变量名用来查找到内存, 变量值就是内存中保存的内容

### 1.8 内存,数据, 变量三者之间的关系

+ 内存是一个容器, 用来存储程序运行需要操作的数据
+ 变量是内存的标识, 我们通过变量找到对应的内存, 进而操作(读/写)内存中的数据

### 1.9 关于引用变量赋值问题

+ 2个引用变量指向同一个对象, 通过一个引用变量修改对象内部数据, 另一个引用变量也看得见

```javascript
var obj1 = {}
  var obj2 = obj1
  obj2.name = 'Tom'
  console.log(obj1.name)
  function f1(obj) {
    obj.age = 12
  }
  f1(obj2)
  console.log(obj1.age)
```

+ 2个引用变量指向同一个对象,让一个引用变量指向另一个对象, 另一个引用变量还是指向原来的对象

```javascript
var obj3 = {name: 'Tom'}
  var obj4 = obj3
  obj3 = {name: 'JACK'}
  console.log(obj4.name)
  function f2(obj) {
    obj = {name: 'Bob'}
  }
  f2(obj4)
  console.log(obj4.name)
```

## 2 对象

### 2.1 什么是对象

+ 代表现实中的某个事物, 是该事物在编程中的抽象
+ 多个数据的集合体(封装体)
+ 用于保存多个数据的容器

### 2.2 为什么要用对象

+ 便于对多个数据进行统一管理

### 2.3 对象的组成

+ 属性：
  + 代表现实事物的状态数据
  + 由属性名和属性值组成
  + 属性名都是字符串类型, 属性值是任意类型
+ 方法：
  + 代表现实事物的行为数据
  + 是特别的属性==>属性值是函数

### 2.4 如何访问对象内部的数据

+ ```shell
  .属性名: 编码简单, 但有时不能用
  ```

+ ```shell
  ['属性名']: 编码麻烦, 但通用
  
   # 什么时候必须使用这个方式：
   # 属性名不是合法的标识名
   # 属性名不确定
  ```

+ 面试题

```javascript
var a = {}
  var obj1 = {n: 2}
  var obj2 = {m: 3}
  console.log(obj1.toString())
  a[obj1] = 4      //a['[object,Object]'] = 4
  a[obj2] = 5      //a['[object,Object]'] = 5
   console.log(a[obj1]) // 输出多少?   5
```

## 3.函数

### 3.1 什么是函数

```shell
具有特定功能的n条语句的封装体 
只有函数是可执行的, 其它类型的数据是不可执行的
函数也是对象
```

### 3.2 为什么要用函数

+ 提高代码复用
+ 便于阅读和交流

### 3.3 定义函数

+ 函数声明
+ 表达式

### 3.4 如何调用（执行）函数

```javascript
test()
new test()
obj.test()
test.call/apply(obj)
```

+ 举例

  ```shell
     #编写程序实现以下功能需求:
      #1. 根据年龄输出对应的信息
      #2. 如果小于18, 输出: 未成年, 再等等!
      #3. 如果大于60, 输出: 算了吧!
      #4. 其它, 输出: 刚好!
  
  ```

  ```javascript
  function showInfo (age) {
      if(age<18) {
        console.log('未成年, 再等等!')
      } else if(age>60) {
        console.log('算了吧!')
      } else {
        console.log('刚好!')
      }
    }
    //调用
    showInfo(17)
    showInfo(22)
  ```

+ 函数也是对象

```javascript
function fn() {

  }
  console.log(fn instanceof Object) // 是Object类型的实例
  console.log(fn.prototype) // 内部有属性
  console.log(fn.call) // 内部有方法
  fn.t1 = 'atguigu' // 可以添加属性
  fn.t2 = function () { // 可以添加方法
    console.log('t2() '+this.t1)
  }
  fn.t2()
```

### 3.5 回调函数

+ 定义：你定义的，你没有直接调用但最终它执行了（在特定条件或时刻）

+ 常见的回调函数

  + DOM事件函数

  ```javascript
   
  <button id="btn">测试点击事件</button>
  
  
  var btn = document.getElementById('btn')
    btn.onclick = function () {
      alert(this.innerHTML)
    }
  ```

  + 定时器函数

  ```javascript
  setInterval(function () {
      alert('到点啦!')
    }, 2000)
  ```

  + ajax回调函数
  + 生命周期回调函数

### 3.6 IIEF

+ 理解：
  + 全称：Immediately-Invoked Function Expression 立即调用函数表达式
  + 别名: 匿名函数自调用
+ 作用：
  + 隐藏内部实现
  + 不污染外部命名空间

```javascript
(function (i) {
    var a = 4
    function fn() {
      console.log('fn ', i+a)
    }
    fn()
  })(3)
```

### 3.7 this关键字

+ this 是什么？
  + 一个关键字，一个内置的引用变量
  + 在函数中都可直接使用 this
  + this 代表调用函数的当前对象
  + 在定义函数时，this还没有确定，只有在执行时才能动态确定（绑定）的
+ 如何确定 this 的值
  + test()
  + obj.test()
  + new test()
  + test.call(obj)      test.apply(obj)

> 本质上任何函数在执行时都是通过某个对象调用的

+ this理解
  + 关键字，不能指定定义变量
  + 本身是一个内置的变量该变量用于指向一个对象
  + this 有两种：全局 this ---> window，局部（函数）this---> 调用其的对象，构造函数 this --->当前构造函数的实例对象。
  + 特殊 this ---> call，apply 强制修改 this

```javascript
window.fun()  // this ---> window
new fun()     // this ---> 实例对象
fun.call(obj) // this ---> obj

//new 操作符  语法：new function（）
// 1.创建空对象
// 2. 执行函数
// 3. 确认 this 的指向： this ---> 创建空对象
// 4. 返回执行结果
```



# 函数高级

## 1. 原型对象

### 1.1 函数的prototype属性

+ 每个函数都有一个 prototype 属性，它默认指向一个Object空对象（即称为：原型对象）
+ 原型对象中有一个属性 constructor ，它指向函数对象

```javascript
<script type = "text/javascript">
function Person() {
    
}
console.log(Person.prototype) //空对象 ---> 原型对象（显示原型对象）
console.log(Person.prototype.constructor) // 函数本身 声明当前的构造器是谁
var person1 = new Person() //生成实例对象
//每一个实例对象身上都有一个属性 _proto_,该属性指向当前实例对象的原型对象（隐式原型对象）
//构造函数的显示原型对象 === 当前构造函数实例对象的隐式原型对象

</script>
```



### 1.2 给原型对象添加属性

> 一般都是方法 

作用：函数的所有实例对象自动拥有原型中的属性（方法）

### 1.3 原型链

```javascript
<script type="text/javascript">
   
  function Fn() {
    this.test1 = function () {
      console.log('test1()')
    }
  }
  Fn.prototype.test2 = function () {
    console.log('test2()')
  }
  var fn = new Fn()

  fn.test1()
  fn.test2()
  console.log(fn.toString())
  fn.test3()
</script>

```

+ 原型链
  + 访问一个对象的属性时，
    + 先在自身属性中查找，找到返回
    + 如果没有，在沿着`_proto_`这条链，向上查找，找到返回
    + 如果最终没找到，返回undefined
  + 别名：隐式原型链
  + 作用：查找对象的属性（方法）

## 2.高级函数

+ filter/map/reduce

  + filter

  ```javascript
  //filter 中的回调函数有一个要求：必须返回一个 boolean 值
  // true:当返回 true 时，函数内部会自动将这次回调的 n 加入到新的数组中
  //false： 当返回 false 时，函数内部会过滤这次的 n
  
  const nums = [10,20,500,40,70,563,222,30]
  let newNums = nums.filter (function (n) {
      return n < 100
  })
  console.log(newNums) //输出数组中小于100的数
  //所以 newNums[10,20,40,70,30]
  
  ```

  + map

  ```javascript
   //接上面 filter 数组
  let new2Nums = newNums.map (function (n) {
      return n *2
  })
  console.log(new2Nums)
  //输出 new2Nums[20,40,80,140,60]
  
  ```

  + reduce

  ```javascript
  //接上面 map 数组
  //作用：对数组中所有的内容进行汇总
  let total = new2Nums.reduce(function (preValue,n){
      return preValue + n
  },0)
  console.log(total)
  
  // 第一次 preValue 0   n 20
  // 第二次 preValue 20  n 40
  // 第三次 preValue 60  n 80
  // 第四次 preValue 140 n 140
  // 第五次 preValue	280 n 60
  // 最后输出 340
  
  ```

  + 为了直接得出上面的340，可以直接写为：

  ```javascript
  let total = nums
  				.filter (function (n) {
                      return n<100
                  })
  				.map (function (n) {
                      return n *2
                  })
  				.reduce (function (preValue,n) {
                     return preValue + n 
                  },0)
  
  ```

  + 使用箭头函数

  ```javascript
  let total = nums.filter(n=>n<100).map(n=>n*2).reduce((preValue,n)=>preValue + n)
  
  ```

  
