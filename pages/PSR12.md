- 示范用例
  collapsed:: true
	- ```PHP
	  <?php
	  
	  declare(strict_types=1);
	  
	  namespace Vendor\Package;
	  
	  use Vendor\Package\{ClassA as A, ClassB, ClassC as C};
	  use Vendor\Package\SomeNamespace\ClassD as D;
	  
	  use function Vendor\Package\{functionA, functionB, functionC};
	  
	  use const Vendor\Package\{ConstantA, ConstantB, ConstantC};
	  
	  class Foo extends Bar implements FooInterface
	  {
	      public function sampleFunction(int $a, int $b = null): array
	      {
	          if ($a === $b) {
	              bar();
	          } elseif ($a > $b) {
	              $foo->bar($arg1);
	          } else {
	              BazClass::bar($arg2, $arg3);
	          }
	      }
	  
	      final public static function bar()
	      {
	          // 方法内容
	      }
	  }
	  ```
- 总则
  collapsed:: true
	- 基本编码标准
		- 代码必须遵循 [PSR-1] 中列出的所有规则
	- 文件
		- 所有 PHP 文件只能使用 Unix LF (换行符) 结尾
		- 所有的 PHP 文件都必须以非空行结尾，以一个 LF 结尾
		- 在仅包含 PHP 代码的文件中，必须省略结尾的 `?>` 标记
	- 代码行
		- 行长度的软限制必须为 120 个字符
		- 行的长度不应超过 80 个字符；超过该长度的行应拆分为多个后续行，每个行的长度不应超过 80 个字符。
		- 行尾不能有尾随空格
		- 每行不能有多个语句
	- 缩进
		- 代码必须为每个缩进级别使用 4 个空格的缩进，并且不能使用缩进标签。
	- 关键词和类型
		- 所有关键词和类型都必须使用小写
	- 类型关键字**必须**使用缩写
		- 使用 `bool` 而不是 `boolean`，使用 `int` 而不是 `integer` 等等。
- 声明、命名空间以及导入
  collapsed:: true
	- 一个 PHP 文件的头部可能会包含多个块。如果包含多个块，则每个块都**必须**用空白行和其他块分隔，并且块内**不能**包含空白行。所有的块都**必须**按照下面的顺序排列，如果不存在该块则忽略。
		- 1.PHP 文件开始标签： `<?php`
		- 2.文件级文档块
		- 3.一个或多个声明语句
		- 4.命名空间声明语句
		- 5.一个或多个基于类的 `use` 声明语句
		- 6.一个或多个基于方法的 `use` 声明语句
		- 7.一个或多个基于常量的 `use` 声明语句
		- 8.其余代码
	- 深度不超过两层符合名称空间
		- ```php
		  <?php
		  #允许最大符合深度
		  use Vendor\Package\SomeNamespace\{
		      SubnamespaceOne\ClassA,
		      SubnamespaceOne\ClassB,
		      SubnamespaceTwo\ClassY,
		      ClassZ,
		  };
		  #不允许
		  use Vendor\Package\SomeNamespace\{
		      SubnamespaceOne\AnotherNamespace\ClassA,
		      SubnamespaceOne\ClassB,
		      ClassZ,
		  };
		  ```
	- 当希望在 PHP 外部包含标记的文件中声明严格类型时打开和关闭标签，声明必须写在文件的第一行并且包含在一个开始的 PHP 标签，以及严格的类型声明和结束标签。
		- ```php
		  <?php declare(strict_types=1) ?>
		  <html>
		  <body>
		      <?php
		          // ... 其他 PHP 代码  ...
		      ?>
		  </body>
		  </html>
		  ```
- 类，属性，和方法
  collapsed:: true
	- 先则
	  collapsed:: true
		- 这里的『类』指的是所有类，接口，以及 trait
		- 任何注释和语句 **不得** 跟在其右花括号后的同一行
		- 当实例化一个类时，后面的圆括号 **必须** 写出来，即使没有参数传进其构造函数
	- 继承和实现
	  collapsed:: true
		- 关键字 `继承` 和 `实现` **必须** 在类名的同一行声明
		- 类的左花括号 **必须** 另起一行；右花括号 **必须** 跟在类主体的下一行
		- 类的左花括号 **必须** 独自成行，且 **不得** 在其上一行或下一行存在空行
		- 右花括号 **必须** 独自成行，且 **不得** 在其上一行存在空行
		- ```php
		  <?php
		  
		  namespace Vendor\Package;
		  
		  use FooClass;
		  use BarClass as Bar;
		  use OtherVendor\OtherPackage\BazClass;
		  
		  class ClassName extends ParentClass implements \ArrayAccess, \Countable
		  {
		      // 常量，属性，方法
		  }
		  ```
		- 如果有接口， `实现` 接口和 `继承`父类 **可以** 分为多行，前者每行需缩进一次。当这么做时，第一个接口 **必须** 写在下一行，且每行 **必须** 只能写一个接口。
		- ```php
		  <?php
		  
		  namespace Vendor\Package;
		  
		  use FooClass;
		  use BarClass as Bar;
		  use OtherVendor\OtherPackage\BazClass;
		  
		  class ClassName extends ParentClass implements
		      \ArrayAccess,
		      \Countable,
		      \Serializable
		  {
		      // 常量，属性，方法
		  }
		  ```
	- 使用trait
	  collapsed:: true
		- 在类里面用于实现 trait 的关键字 `use` **必须** 在左花括号的下一行声明。
		- ```php
		  <?php
		  
		  namespace Vendor\Package;
		  
		  use Vendor\Package\FirstTrait;
		  
		  class ClassName
		  {
		      use FirstTrait;
		  }
		  ```
		- 每个导入类的 trait **必须** 每行一个包含声明，且每个包含声明 **必须** 有其 `use` 导入语句
		- ```php
		  <?php
		  
		  namespace Vendor\Package;
		  
		  use Vendor\Package\FirstTrait;
		  use Vendor\Package\SecondTrait;
		  use Vendor\Package\ThirdTrait;
		  
		  class ClassName
		  {
		      use FirstTrait;
		      use SecondTrait;
		      use ThirdTrait;
		  }
		  ```
		- 在类文件中，如果在使用’use Trait’之后没有其他内容了 ，类名右大括号必须另起一行
		- ```php
		  <?php
		  
		  namespace Vendor\Package;
		  
		  use Vendor\Package\FirstTrait;
		  
		  class ClassName
		  {
		      use FirstTrait;
		  }
		  ```
		- 如有其他内容，两者之间需空一行
		- ```php
		  <?php
		  
		  namespace Vendor\Package;
		  
		  use Vendor\Package\FirstTrait;
		  
		  class ClassName
		  {
		      use FirstTrait;
		  
		      private $property;
		  }
		  ```
		- 当使用’ insteadof ‘和’ as ‘运算符时，它们必须如图所示使用，注意缩进、间距和另起一行
		- ```php
		  <?php
		  
		  class Talker
		  {
		      use A, B, C {
		          B::smallTalk insteadof A;
		          A::bigTalk insteadof C;
		          C::mediumTalk as FooBar;
		      }
		  }
		  ```
	- 属性和常量
	  collapsed:: true
		- 所有属性 **必须** 声明可见性
		- 所有常量 **必须** 声明可见性
		- 关键字 `var` **不得** 用于声明属性
		- 每条声明语句 **不得** 声明多于一个属性
		- 属性名 **不得** 用单个下划线开头表明其受保护的或私有的可见性
		- 类型声明和属性名之间 **必须** 有一个空格
		- ```php
		  <?php
		  
		  namespace Vendor\Package;
		  
		  class ClassName
		  {
		      public $foo = null;
		      public static int $bar = 0;
		  }
		  ```
	- 方法和函数
	  collapsed:: true
		- 所有的方法 **必须** 事先声明类型
		- 方法命名 **一定不可** 用单个下划线来区分是 `protected` 或 `private` 类型
		- 方法和函数名称中，方法命名后面 **一定不可** 使用空格。方法开始的花括号 **必须** 写在方法声明后自成一行， 结束花括号也 **必须** 写在方法后面自成一行。开始左括号后和结束右括号前，都 **一定不可** 有空格符。
		- ```php
		  <?php
		  
		  namespace Vendor\Package;
		  
		  class ClassName
		  {
		      public function fooBarBaz($arg1, &$arg2, $arg3 = [])
		      {
		          // 方法主体
		      }
		  }
		  ```
		- ```php
		  <?php
		  
		  function fooBarBaz($arg1, &$arg2, $arg3 = [])
		  {
		      // 函数主体
		  }
		  ```
		- 在参数列表中， **不得** 在每个逗号前存在空格，且 **必须** 在每个逗号后有一个空格。
		- 方法和函数中带有默认值的参数 **必须** 放在参数列表的最后。
		- ```php
		  <?php
		  
		  namespace Vendor\Package;
		  
		  class ClassName
		  {
		      public function foo(int $arg1, &$arg2, $arg3 = [])
		      {
		          // 方法主体
		      }
		  }
		  ```
		- 参数列表 可以 分为多行，每行参数缩进一次。当这么做时，第一个参数 必须 放在下一行，且每行 必须 只能有一个参数。当参数列表分成多行时，右圆括号和左花括号 必须 放在同一行且单独成行，两者之间存在一个空格。
		- ```php
		  <?php
		  
		  namespace Vendor\Package;
		  
		  class ClassName
		  {
		      public function aVeryLongMethodName(
		          ClassTypeHint $arg1,
		          &$arg2,
		          array $arg3 = []
		      ) {
		          // 方法主体
		      }
		  }
		  ```
			- 当你定义一个返回值类型声明时，冒号后面的类型声明 **必须** 用空格符隔开。冒号和声明 **必须** 在同一行，且跟参数列表后的结束括号之间没有空格。
			- ```php
			  <?php
			  
			  declare(strict_types=1);
			  
			  namespace Vendor\Package;
			  
			  class ReturnTypeVariations
			  {
			      public function functionName(int $arg1, $arg2): string
			      {
			          return 'foo';
			      }
			  
			      public function anotherFunction(
			          string $foo,
			          string $bar,
			          int $baz
			      ): string {
			          return 'foo';
			      }
			  }
			  ```
				- 在可空类型声明中，问号和类型声明之间**不能**有空格
				- ```php
				  <?php
				  
				  declare(strict_types=1);
				  
				  namespace Vendor\Package;
				  
				  class ReturnTypeVariations
				  {
				      public function functionName(?string $arg1, ?int &$arg2): ?string
				      {
				          return 'foo';
				      }
				  }
				  ```
					- 当在参数之前使用引用运算符 `&` 时，引用运算符之后**不能**有空格，例如上面的示例。可变参数声明的三个点和参数名称之间**不能**有空格：
					- ```php
					  public function process(string $algorithm, ...$parts)
					  {
					      // 函数体
					  }
					  ```
						- 当同时使用引用运算符和可变参数运算符时，它们之间**不能**有任何空格：
						- ```php
						  public function process(string $algorithm, &...$parts)
						  {
						      // 函数体
						  }
						  ```
							- 如果是 `abstract` and `final` ，那么申明的时候**必须**是可见性声明,如果是 `static` ，声明**必须**位于可见性声明之后。
							- ```php
							  <?php
							  
							  namespace Vendor\Package;
							  
							  abstract class ClassName
							  {
							      protected static $foo;
							  
							      abstract protected function zim();
							  
							      final public static function bar()
							      {
							          // 请求体
							      }
							  }
							  ```
								- 当我们在进行方法或者函数调用的时候，方法名或函数名与左括号之间**不能**出现空格，在右括号之后也**不能**出现空格，并且在右括号之前也**不能**有空格。在参数列表中，每个逗号前面**不能**有空格，每个逗号后面**必须**有一个空格
								- ```php
								  <?php
								  
								  bar();
								  $foo->bar($arg1);
								  Foo::bar($arg2, $arg3);
								  ```
									- 参数列表可以分为多行，每行后面缩进一次。这样做时，列表中的第一项必须位于下一行，并且每一行必须只有一个参数。跨多个行拆分单个参数 (就像匿名函数或者数组那样) 并不构成拆分参数列表本身
									- ```php
									  <?php
									  
									  $foo->bar(
									      $longArgument,
									      $longerArgument,
									      $muchLongerArgument
									  );
									  
									  somefunction($foo, $bar, [
									    // ...
									  ], $baz);
									  
									  $app->get('/hello/{name}', function ($name) use ($app) {
									      return 'Hello ' . $app->escape($name);
									  });
									  ```
- 流程控制
  collapsed:: true
	- 总则
	  collapsed:: true
		- 流程控制关键词之后 必须 要有一个空格
		- 左括号后面 不能 有空格
		- 右括号前面 不能 有空格
		- 右括号与左大括号之间 必须 要有一个空格
		- 流程主体 必须 要缩进一次
		- 流程主体 必须 在左大括号之后另起一行
		- 右大括号 必须 在流程主体之后另起一行
	- `if` ,   `elseif` ,   `else`
	  collapsed:: true
		- ```php
		  <?php
		  
		  if ($expr1) {
		      // if body
		  } elseif ($expr2) {
		      // elseif body
		  } else {
		      // else body;
		  }
		  
		  if (
		      $expr1
		      && $expr2
		  ) {
		      // if body
		  } elseif (
		      $expr3
		      && $expr4
		  ) {
		      // elseif body
		  }
		  ```
	- `switch` ,   `case`
	  collapsed:: true
		- ```php
		  <?php
		  
		  switch ($expr) {
		      case 0:
		          echo 'First case, with a break';
		          break;
		      case 1:
		          echo 'Second case, which falls through';
		          // no break
		      case 2:
		      case 3:
		      case 4:
		          echo 'Third case, return instead of break';
		          return;
		      default:
		          echo 'Default case';
		          break;
		  }
		  ```
	- `while` ,   `do while`
	  collapsed:: true
		- ```php
		  <?php
		  
		  while ($expr) {
		      // structure body
		  }
		  
		  while (
		      $expr1
		      && $expr2
		  ) {
		      // structure body
		  }
		  
		  do {
		      // structure body;
		  } while ($expr);
		  
		  do {
		      // structure body;
		  } while (
		      $expr1
		      && $expr2
		  );
		  ```
	- `for`
	  collapsed:: true
		- ```php
		  <?php
		  
		  for ($i = 0; $i < 10; $i++) {
		      // for body
		  }
		  
		  for (
		      $i = 0;
		      $i < 10;
		      $i++
		  ) {
		      // for body
		  }
		  ```
	- `foreach`
	  collapsed:: true
		- ```php
		  <?php
		  
		  foreach ($iterable as $key => $value) {
		      // 迭代主体
		  }
		  ```
	- `try`   ，   `catch`   ，   `finally`
	  collapsed:: true
		- ```php
		  <?php
		  
		  try {
		      // try 主体
		  } catch (FirstThrowableType $e) {
		      // 捕获异常主体
		  } catch (OtherThrowableType | AnotherThrowableType $e) {
		      // 捕获异常主体
		  } finally {
		      // finally 主体
		  }
		  ```
- 运算符
  collapsed:: true
	- 一元运算符
		- ```php
		  $i++;
		  ++$j;
		  $intValue = (int) $input;
		  ```
	- 二元运算符
		- ```php
		  if ($a === $b) {
		      $foo = $bar ?? $a ?? $b;
		  } elseif ($a > $b) {
		      $foo = $a + $b * $c;
		  }
		  ```
	- 三元运算符
		- ```php
		  $variable = $foo ? 'foo' : 'bar';
		  $variable = $foo ?: 'bar';
		  ```
	- 闭包
		- ```php
		  <?php
		  
		  $closureWithArgs = function ($arg1, $arg2) {
		      // 函数体
		  };
		  
		  $closureWithArgsAndVars = function ($arg1, $arg2) use ($var1, $var2) {
		      // 函数体
		  };
		  
		  $closureWithArgsVarsAndReturn = function ($arg1, $arg2) use ($var1, $var2): bool {
		      // 函数体
		  };
		  ```
		- ```php
		  <?php
		  
		  $longArgs_noVars = function (
		      $longArgument,
		      $longerArgument,
		      $muchLongerArgument
		  ) {
		     // body
		  };
		  
		  $noArgs_longVars = function () use (
		      $longVar1,
		      $longerVar2,
		      $muchLongerVar3
		  ) {
		     // body
		  };
		  
		  $longArgs_longVars = function (
		      $longArgument,
		      $longerArgument,
		      $muchLongerArgument
		  ) use (
		      $longVar1,
		      $longerVar2,
		      $muchLongerVar3
		  ) {
		     // body
		  };
		  
		  $longArgs_shortVars = function (
		      $longArgument,
		      $longerArgument,
		      $muchLongerArgument
		  ) use ($var1) {
		     // body
		  };
		  
		  $shortArgs_longVars = function ($arg) use (
		      $longVar1,
		      $longerVar2,
		      $muchLongerVar3
		  ) {
		     // body
		  };
		  ```
	- ```php
	  <?php
	  
	  $foo->bar(
	      $arg1,
	      function ($arg2) use ($var1) {
	          // body
	      },
	      $arg3
	  );
	  ```
- 匿名类
  collapsed:: true
	- ```php
	  <?php
	  
	  $instance = new class {};
	  
	  // 花括号在同一行
	  $instance = new class extends \Foo implements \HandleableInterface {
	      // 类内容
	  };
	  
	  // 花括号在下一行
	  $instance = new class extends \Foo implements
	      \ArrayAccess,
	      \Countable,
	      \Serializable
	  {
	      // 类内容
	  };
	  ```