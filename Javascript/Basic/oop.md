# OOP 面向对象编程 
* 面向对象编程希望把所有的事物都认为是一个对象，而对象可以通过实例化一个类或继承一个对象而获得（函数式编程认为一切皆函数，一个确定的输入对应一个确定的输出，并且不会产生副作用）。

> ### 面向对象的三大特性: 封装, 继承, 多态。
***
## 封装
*是指面向对象的编程语言中隐藏了某一方法的内部逻辑或某一属性的值。对象只对外提供与其它对象交互所必需的接口，我们只需要关注如何使用，而不需要关心这些方法和属性究竟是什么

> 优点:
* 对内部数据起到一定保护
* 提高内聚，降低耦合（可以被多种对象复用）

* 函数模式
* 自面量模式
* 工厂模式
* 构造函数模式让她涛涛涛涛涛涛涛涛涛涛涛涛涛涛涛涛他愿意
* 原型模式
***
## 继承
* 原型链继承
* 构造函数继承(经典继承)
* 组合式继承
* 原型式继承
* 寄生组合式继承
* 混入式继承
***
## 多态
> 多态意味着某个方法在不同的条件下会选择不同的动作。多态性包括以下两种特性：
* 重写（Overwrite）：允许子类对方法的实现重写，但签名、形式参数列表和返回值类型都不能改变
* 重载（Override）：允许子类改变方法的形式参数列表、返回值类型，但不允许改变签名，在调用方法时，根据输入的形式参数选择对应的重载