# 数据类型

|  基本数据类型   |  引用数据类型  |
|  ---- | ---- |
| number  | Object (Function, Date, Array) |
| string  |
| boolean  |
| null  |
| undefined  |
| Symbol (es6)  | 
| BigInt (es10)  |
| 值保存在栈空间,我们通过按值来访问的 | 值是对象，栈内存中存放地址指向堆内存中的对象。是按引用访问的。栈内存中存放的只是该对象的访问地址，在堆内存中为这个值分配空间|

## 区别
1. 基本数据类型不可以添加/删除属性和方法
2. 复制的方式不同；引用类型复制的时候，复制的是指针，2个变量实际指的是同一个对象
3. 函数的参数是按值传递的
***

## 检测数据类型
1. ### typeOf (检测基本数据类型及Object, function)
<!-- 检测基本数据类型唯一例外 -->
```
typeof null === 'object'
```
2. ### instanceof(运算符用来测试一个对象在其原型链中是否存在一个构造函数的 prototype 属性)

3. ### 最万能的检测方法
```
Object.prototype.toString.call();
```
***

## 类型转化