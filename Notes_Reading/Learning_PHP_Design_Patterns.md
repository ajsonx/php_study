# Learning PHP 设计模式

- *中国电力出版社*  
- *翻译有点烂，一搜书评 同感的人不在少数。*
- *不太严谨，本书74和75页的插图是一样的。*
- *本书实例很多，代码基本占了书的篇幅一半。*

作为设计模式入门书籍看吧。之前了解了很多概念，跟着书操作一遍。

电力出版社很多书都翻译的不好，还是人民邮电出版社比较好。拔草。

本书讲了非常多的概念，比较简单易懂（有基础）

以下读书笔记 不保证包含全书知识点 **尽量使用一句话的形式来概括一个概念，大部分摘选书中的语言，少部分使用自己的理解。**

如果需要代码辅以说明会给出链接。以下按章节记录。

代码使用sublime编写，没有代码提示，部分简答易懂的代码没有运行过，可能会出现错误，谅解。




## 第一章·PHP与面向对象编程

> 不要期望工作适合你的能力，而要祈望自己的能力去适应工作。
>

* 模块化：一个问题分解为小的问题 <!--这个解释也可以说是分治、动态规划、二分...这说明了解决问题的方法在不同领域虽然有不同的叫法，但是模式是一样的。注重培养解决问题的思维。-->

* 单一职责原则：一个类应当只有一个原则

* Client类作为请求者
	
	一开始也不清楚作者or翻译想要表达的意思，结合代码发现其实就是：(使用Client类调用具体的功能类)[http://]
	
* OOP和设计模式的主要作用之一就是能够改变单个模块而不会破坏整个程序

* 算法处理的是操作速度，而设计模式解决的是开发速度

* 即时回报还是长期回报取决于设计的代价

## 第二章·OOP基本概念

### 抽象

* 抽象abstract：指示一个对象的基本特征，使它与所有其他对象区分开，从而从查看者的角度提供了清晰定义的概念边界。
  在某种程度上，所有类都是对数据的一组操作的抽象
  抽象是用来处理复杂性的主要工具，问题越复杂，越需要抽象来解决。

* 抽象类特点：
	
	1.抽象类不能实例化，只能继承
	
	2.一个类至少有一个抽象方法，必然是一个抽象类
	

3.与抽象方法不同，不强制使用这些抽象属性
	

	4.子类必须实现父类的抽象方法
	
	5.抽象类中可以有普通方法

### 接口

* 接口interface：

  1.接口中不能包含变量，可以包含常量 使用作用域解析符(::)

  2.接口中不能包含具体方法和属性 ？？？try

  3.

* Citrus 柑橘类水果


### 封装

* 封装就是划分一个抽象的诸多元素的过程，封装的作用就是将抽象的契约接口与其实现分离

* [通过可见性保护封装]() try
* 获取和设置 Getters Setters：允许公开访问获取方法和设置方法只会破坏封装

> 要修改一个过程，只需要重新组织消息序列，而不是改变一个过程 ——OOP

### 继承

* 继承抽象类，注重使用浅继承，只有一层子类，减少破坏

### 多态

* 多态的真正价值：可以调用相同接口的对象来完成不同的工作
* 接口（父类）的不同实现方式
* php7中可以声明返回类型
* 设计模式中已经充分内建有多态性

## 第三章·基本设计模式概念

### MVC模式

* 模型-视图-控制器
* MVC的<u>*表现部分*</u>有两个元素：视图和控制器。视图是一个窗口，模型提供数据，控制器提供打开和关闭数据，并发送到视图。

### 设计模式基本原则

这里写的也是让我一脸懵逼，只写了两个基本原则。



1. 
2. 按接口而不是按实现来编程

 

