# typescript

## 1. 安装

安装：**npm i typescript -g**

版本：**typescript -v**

## 2.使用及转成 js

1. 新建 **ts** 文件
2. 命令行输入命令：**tsc 文件名** 转换为 js 文件，下面会多一个 js 文件
3. 在 node 环境运行 js 文件

## 3. 基本数据类型

1. 字符串

   ```typescript
   let dogName:string = '旺财'
   let dogSex:string = '公'
   let dogAge:number = 6
   let introDog:string = `我有一只狗，他叫${dogName},今年${dogAge},是${dogSex}的`
   console.log(introDog)
   ```

2. 数字

   ````typescript
   //2 8 10 16
   let num1:number = 16
   let num2:number = 0o20
   let num3:number = 0x10
   let num4:number = 0b10000
   console.log(num1,num2,num3,num4)
   ````

3. 布尔

   ```typescript
   let flag:boolean = false
   console.log(flag)
   ```

4. 数组

   ````typescript
   //数字数组
   let numArr:number = [1,2,3]
   //字符串数字
   let strArr:string = ['zjg'，'mz']
   //布尔数组
   let boolArr:Array<boolean> = [true,false]
   ````

5. 元组

   ````typescript
   let tuple:[string,number,boolean,string]
   tuple = ['北京',100,true,'zjg'] //ok
   tuple = [aaa,100,true,'zjg'] //报错
   tuple = ['北京',100,true,'zjg',10]//可以打印，但结果不可预测
   console.log(tuple)
   
   //取元素
   let tuple:[string,number,boolean,string] = ['北京',100.222,true,'zjg']
   console.log(tuple[1].toFixed())//他会自动判断类型，然后可以直接使用各个类型的方法
   console.log(tuple[0].trim())//字符串方法
   ````

   
