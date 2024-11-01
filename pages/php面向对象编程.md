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
  collapsed:: true
	- 子类会继承父类所有 public 和 protected 的方法，属性和常量
- 10.范围解析操作符（::）
  collapsed:: true
	- 是一种允许访问类或其中一个父类的[常量](https://www.php.net/manual/zh/language.oop5.constants.php)、[static](https://www.php.net/manual/zh/language.oop5.static.php) 属性或 [static](https://www.php.net/manual/zh/language.oop5.static.php) 方法的标记
- 11.静态（static）关键字
  collapsed:: true
	- 声明类属性或方法为静态，就可以不实例化类而直接访问
	- 静态属性
		- 使用`::`访问不能通过`->`访问
- 12.抽象类
  collapsed:: true
	- 是一种不能直接实例化的类
	- 作用是提供一个模板或者基类，供其他子类继承和实现
	- 它主要用来定义通用的接口和基本行为，让子类在此基础上实现具体的功能
	- 当你有一组具有共同特征的类时，可以使用抽象类作为它们的基类，比如所有动物都具有的某些通用属性和行为
	- ```php
	  abstract class Vehicle {
	      protected $speed;
	  
	      public function setSpeed($speed) {
	          $this->speed = $speed;
	      }
	  
	      // 抽象方法，子类必须实现
	      abstract public function start();
	  
	      abstract public function stop();
	  }
	  
	  class Car extends Vehicle {
	      public function start() {
	          echo "Car is starting at speed $this->speed.\n";
	      }
	  
	      public function stop() {
	          echo "Car has stopped.\n";
	      }
	  }
	  
	  class Bike extends Vehicle {
	      public function start() {
	          echo "Bike is starting at speed $this->speed.\n";
	      }
	  
	      public function stop() {
	          echo "Bike has stopped.\n";
	      }
	  }
	  
	  // 实例化
	  $car = new Car();
	  $car->setSpeed(60);
	  $car->start(); // 输出: Car is starting at speed 60.
	  $car->stop();  // 输出: Car has stopped.
	  
	  $bike = new Bike();
	  $bike->setSpeed(20);
	  $bike->start(); // 输出: Bike is starting at speed 20.
	  $bike->stop();  // 输出: Bike has stopped.
	  
	  ```
- 13.对象接口
  collapsed:: true
	- 接口只定义方法的名称和参数，而不包含具体实现（更加严格）
	- 当你有一些与具体实现无关的行为或能力，并希望不同的类实现这些行为时，使用接口更合适
	- 抽象类是一个有基本实现的模板，用于在具有共同属性的类中提供基础代码复用
	- 接口更像一个行为上的契约，保证实现接口的类都能提供特定的功能
	- ```php
	  interface Flyable {
	      public function fly(); // 接口方法，必须实现
	  }
	  
	  interface Swimmable {
	      public function swim();
	  }
	  
	  class Duck implements Flyable, Swimmable {
	      public function fly() {
	          echo "Duck is flying.\n";
	      }
	  
	      public function swim() {
	          echo "Duck is swimming.\n";
	      }
	  }
	  ```
	-
	-
- 14.Traits
  collapsed:: true
	- 一种代码复用机制，它允许我们在类中包含共享的代码，而不需要通过继承的方式
	- 决了单继承的局限性，使类能够在不继承多个基类的情况下重用多个独立的代码块
	- 当你需要多个类共享相同的功能，但这些类之间没有直接的父子关系
	- 当功能需要跨越多个类、多个层次结构时（如日志、权限等通用功能），Traits 提供了更好的代码复用性
	- ```php
	  trait A {
	      public function sayHello() {
	          echo "Hello from A\n";
	      }
	  }
	  
	  trait B {
	      public function sayHello() {
	          echo "Hello from B\n";
	      }
	  }
	  
	  class MyClass {
	      use A, B {
	          A::sayHello insteadof B; // 使用A中的sayHello方法
	          B::sayHello as sayHelloFromB; // 将B中的sayHello方法改名
	      }
	  }
	  
	  $myObject = new MyClass();
	  $myObject->sayHello(); // 输出: Hello from A
	  $myObject->sayHelloFromB(); // 输出: Hello from B
	  ```
- 15.匿名类
  collapsed:: true
	- 一种没有名字的类，通常用来定义一次性使用的类
	- ```php
	  $object = new class {
	      public function sayHello() {
	          echo "Hello from anonymous class!";
	      }
	  };
	  $object->sayHello(); // 输出: Hello from anonymous class!
	  ```
	- 匿名类继承和实现接口
	- ```php
	  interface Logger {
	      public function log($message);
	  }
	  
	  $logger = new class implements Logger {
	      public function log($message) {
	          echo "Logging message: $message";
	      }
	  };
	  
	  $logger->log("This is a log message."); // 输出: Logging message: This is a log message.
	  
	  ```
	- 使用场景
	  collapsed:: true
		- **一次性对象**：当需要一个只使用一次的对象，不需要为它创建单独的类文件
		- **简化代码**：在测试、快速原型开发或短期脚本中，可以使用匿名类简化代码结构
		- **依赖注入或临时实现接口**：可以用匿名类来注入特定接口的实现，或在不影响代码结构的情况下测试不同的实现
		- **闭包替代**：有时候匿名类可以替代闭包，尤其是需要复杂的行为时。匿名类相比闭包更具结构性，且支持方法和属性
		- 示例
			- ```php
			  function processTask($taskName) {
			      $logger = new class {
			          public function log($message) {
			              echo "[LOG] $message\n";
			          }
			      };
			  
			      $logger->log("Starting task: $taskName");
			      // 执行任务逻辑
			      $logger->log("Task $taskName completed");
			  }
			  
			  processTask("ImportData");
			  // 输出：
			  // [LOG] Starting task: ImportData
			  // [LOG] Task ImportData completed
			  
			  ```
- 16.重载
  collapsed:: true
	- 在PHP中，**重载**（Overloading）指的是在运行时动态地创建属性和方法
	- `__get()`、`__set()`、`__call()`
	- demo:动态属性的重载
		- ```php
		  class Person {
		      private $data = [];
		  
		      // 动态获取属性
		      public function __get($name) {
		          return $this->data[$name] ?? "Property {$name} does not exist.";
		      }
		  
		      // 动态设置属性
		      public function __set($name, $value) {
		          $this->data[$name] = $value;
		      }
		  }
		  
		  $person = new Person();
		  $person->name = "Alice"; // 调用 __set()
		  echo $person->name;      // 调用 __get() 输出: Alice
		  echo $person->age;       // 输出: Property age does not exist.
		  ```
	- 示例：动态方法的重载
		- ```php
		  class MagicMethods {
		      public function __call($name, $arguments) {
		          echo "Calling method '$name' with arguments: " . implode(', ', $arguments) . "\n";
		      }
		  
		      public static function __callStatic($name, $arguments) {
		          echo "Calling static method '$name' with arguments: " . implode(', ', $arguments) . "\n";
		      }
		  }
		  
		  $obj = new MagicMethods();
		  $obj->doSomething("arg1", "arg2");    // 调用 __call()
		  MagicMethods::doSomethingElse("argA"); // 调用 __callStatic()
		  ```
- 17.遍历对象
  collapsed:: true
	- `foreach`
- 18.魔术方法
  collapsed:: true
	- **魔术方法**（Magic Methods）是以双下划线 (`__`) 开头的一组特殊方法，主要用来增强对象的动态行为
- 19.final
  collapsed:: true
	- 通过在定义方法、属性和常量之前加上 `final` 来防止被子类覆盖
	-
- 20.对象复制
  collapsed:: true
	- 是通过克隆（`clone`）关键词来创建一个现有对象的副本
	- ```php
	  class Person {
	      public $name;
	  
	      public function __construct($name) {
	          $this->name = $name;
	      }
	  }
	  
	  $original = new Person("Alice");
	  $copy = clone $original;
	  
	  $copy->name = "Bob";
	  
	  echo $original->name; // 输出: Alice
	  echo $copy->name;     // 输出: Bob
	  ```
- 21.对象比较
- 22.后期静态绑定
  collapsed:: true
	- 解决了继承层级中类的静态引用问题
	- 这个特性允许子类在调用父类方法时，能够“绑定”到当前实际调用的类，而不是被绑定到定义该方法的父类
- 23.序列化
  collapsed:: true
	- **序列化**和**反序列化**是一种将对象或数据结构转换为字符串格式以便保存、传输或恢复的过程
	-
- 24.协变和逆变
  collapsed:: true
	- **协变**：在子类中**返回类型可以更具体**（即更加严格）。例如，如果父类的方法返回一个 `Animal` 类型，子类的方法可以返回 `Dog` 类型（`Dog` 是 `Animal` 的子类）。
	- **逆变**：在子类中**参数类型可以更宽泛**（即更加松散）。例如，如果父类的方法参数类型是 `Dog` 类型，子类的方法可以接收 `Animal` 类型作为参数（`Animal` 是 `Dog` 的父类）。
	- ```php
	  class Animal {
	      public function getAnimal(): Animal {
	          return new Animal();
	      }
	  }
	  
	  class Dog extends Animal {
	      // 返回类型可以更加具体，返回 Dog 类型而不是 Animal
	      public function getAnimal(): Dog {
	          return new Dog();
	      }
	  }
	  class AnimalHandler {
	      public function handle(Animal $animal) {
	          echo "Handling an animal";
	      }
	  }
	  
	  class DogHandler extends AnimalHandler {
	      // 参数类型可以更加宽泛，接收 Animal 类型
	      public function handle($animal) {
	          echo "Handling an animal or dog";
	      }
	  }
	  ```