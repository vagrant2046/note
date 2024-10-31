- #php
- 1.简介
  collapsed:: true
	- php具有完整的对象模型：访问控制、抽象类、final类、魔术方法、接口、对象复制
- 2.基本概念
  collapsed:: true
	- 类（class）
		- 类似一个模具或者蓝图，描述一类事物的`特征`和`行动`
			- 特征：具有什么特性（`属性`）
			- 行为：能够做什么事情（`方法`）
	- 对象（Object）
		- 根据这个模具或者蓝图可以制作很多符合要求的物品，每个物品就是这个类的实例，称为`对象`
	- 属性（Properties）
	  id:: 6722f4cb-4f4f-476e-b3c7-add8d46549a5
		- 存储类中的变量
		  id:: 672318e0-ae0e-4fb4-b54a-af3a3a93ada5
	- 方法（Methods）
		- 类中定义的函数，用于操作属性或执行动作
	- 封装 （Encapsulation）
		- 将数据和方法放在同一个类中，限制直接访问
	- 继承（extend）
		- 允许一个类继承另一个类的属性和方法
	- 多态（Polymorphism）
		- 允许不同的对象使用相同的接口进行操作
- 3.属性
  collapsed:: true
	- ((672318e0-ae0e-4fb4-b54a-af3a3a93ada5))
- 4.类常量
  collapsed:: true
	- 类中始终保持不变的值定义为常量
	- 类常量的访问 `::`
		- ```php
		  echo $classname::CONSTANT
		  ```
- 5.类的自动加载
  collapsed:: true
	- [spl_autoload_register()](https://www.php.net/manual/zh/function.spl-autoload-register.php) 函数可以注册任意数量的自动加载器，当使用尚未被定义的类（class）和接口（interface）时自动去加载
	  collapsed:: true
		- ```php
		  <?php
		  spl_autoload_register(function ($class_name) {
		      require_once $class_name . '.php';
		  });
		  
		  $obj  = new MyClass1();
		  $obj2 = new MyClass2();
		  ```
- 6.构造函数
  collapsed:: true
	- 具有构造函数的类会在每次创建新对象时先调用此方法，所以非常适合在使用对象之前做一些初始化工作
	- [__construct()](https://www.php.net/manual/zh/language.oop5.decon.php#object.construct)
- 7.析构函数
  collapsed:: true
	- 析构函数会在到某个对象的所有引用都被删除或者当对象被显式销毁时执行
	- `__destruct()`
- 8.访问控制性
  collapsed:: true
	- public
		- 可以在任何地方被访问
	- protected
		- 可以被其自身以及其子类和父类访问
	- private
		- 只能被其定义所在的类访问
- 9.对象继承
	-