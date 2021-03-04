# JavaScript 教程

## 1.为什么学习JavaScript

> **HTML** 定义了网页的内容
>
> **CSS** 描述了网页的布局
>
> **JavaScript** 网页的行为

## 2.ECMAScripty版本

| 年份 | 名称           | 描述                                              |
| :--- | :------------- | :------------------------------------------------ |
| 1997 | ECMAScript 1   | 第一个版本                                        |
| 1998 | ECMAScript 2   | 版本变更                                          |
| 1999 | ECMAScript 3   | 添加正则表达式 添加 try/catch                     |
|      | ECMAScript 4   | 没有发布                                          |
| 2009 | ECMAScript 5   | 添加 "strict mode"，严格模式 添加 JSON 支持       |
| 2011 | ECMAScript 5.1 | 版本变更                                          |
| 2015 | ECMAScript 6   | 添加类和模块                                      |
| 2016 | ECMAScript 7   | 增加指数运算符 (**) 增加 Array.prototype.includes |

>*ECMAScript 6 也称为 ECMAScript 2015。*
>
>*ECMAScript 7 也称为 ECMAScript 2016。*

## 3.JavaScript语法

### 3.1字面量

1. 数字（Number）字面量：整数、小数、科学计数
2. 字符串（String）字面量：单引号或双引号
3. 表达式字面量：5+6
4. 数组（Array）字面量：[40,100,1,5]
5. 对象（Object）字面量：{firstName:"John", lastName:"Doe"}
6. 函数（Function）字面量：function myFunction(a, b) { return a * b;}

### 3.2变量

> 变量用于存储数据值，js中使用关键字var来定义变量，使用等号来为变量赋值

~~~js
var x,length;
x = 5;
length = 6;
~~~

### 3.3操作符

| 类型                   | 实例      | 描述                   |
| :--------------------- | :-------- | :--------------------- |
| 赋值，算术和位运算符   | = + - * / | 在 JS 运算符中描述     |
| 条件，比较及逻辑运算符 | == != < > | 在 JS 比较运算符中描述 |

### 3.4保留关键字

| abstract | else       | instanceof |    super     |
| -------- | ---------- | ---------- | :----------: |
|          |            |            |              |
| boolean  | enum       | int        |    switch    |
|          |            |            |              |
| break    | export     | interface  | synchronized |
|          |            |            |              |
| byte     | extends    | let        |     this     |
|          |            |            |              |
| case     | false      | long       |    throw     |
|          |            |            |              |
| catch    | final      | native     |    throws    |
|          |            |            |              |
| char     | finally    | new        |  transient   |
|          |            |            |              |
| class    | float      | null       |     true     |
|          |            |            |              |
| const    | for        | package    |     try      |
|          |            |            |              |
| continue | function   | private    |    typeof    |
|          |            |            |              |
| debugger | goto       | protected  |     var      |
|          |            |            |              |
| default  | if         | public     |     void     |
|          |            |            |              |
| delete   | implements | return     |   volatile   |
|          |            |            |              |
| do       | import     | short      |    while     |
|          |            |            |              |
| double   | in         | static     |     with     |
|          |            |            |              |

### 3.5注释

~~~js
//单行注释
/*
 *多行注释
*/
~~~

###　3.6函数

~~~js
function myFunction(a,b){
    return a*b;
}
~~~

###　3.7字母大小写

> 对大小写敏感

### 3.8字符集

> 使用Unicode字符集

## 4.JavaScript数据类型

### 4.1值类型（基本类型）

> 1. 字符串（String）
> 2. 数字（Number）
> 3. 布尔值（Boolean）
> 4. 对空（Null）
> 5. 未定义（Undefined）
> 6. Symbol（ES6引入表示独一无二的值）

## 4.2引用数据类型

> 1. 对象（Object）
> 2. 数组（Array）
> 3. 函数（Function）



## 5.对象

> 对象有它的属性（如汽车都有重量、颜色等属性，启动、停止等方法）
>
> 所有的汽车都有这些属性，但是每款车的属性都不尽相同
>
> 所有的汽车都拥有这些方法，但是它们被执行的时间不尽相同

~~~js
//访问对象属性
person.lastName;
persion['lastname'];
//访问对象方法
name = person.fullname();
//创建对象方法
var demo = {
    methodName : function(){
        //代码
    }
}
~~~

## 6.函数

~~~js
function functionname(var1,var2)
{
    //执行代码
}
~~~

### 6.1局部变量、全局变量、生存周期

> 1. 局部变量：函数内部声明的变量，函数内部才可以访问
> 2. 全局变量：函数外部声明的变量，所有脚本都可以访问
> 3. 生存周期：局部变量（声明开始，函数运行后结束），全局变量（声明开始，页面关闭后结束）
> 4. 非严格模式下给未声明变量赋值创建的全局变量是可配置属性，可以删除。



## 7.作用域

>为可访问变量，对象，函数的集合

~~~js
//局部作用域（变量在函数内声明，只能在函数内部访问。）
//函数外部不能调用 carName 变量
function myFunction(){
    var carName = 'Volvo';
    //函数内可以调用carName变量
}

//全局变量（在函数外定义，网页中的所有脚本均可使用）
var carName = " Volvo";
// 此处可调用 carName 变量
function myFunction() {
    // 函数内可调用 carName 变量
}

//如果变量在函数内没有声明（没有使用 var 关键字），该变量为全局变量。
// 此处可调用 carName 变量
function myFunction() {
    carName = "Volvo";
    // 此处可调用 carName 变量
}
~~~

## 8.事件

> 发生在HTML上的事情

~~~js
<some-HTML-element some-event='JavaScript 代码'>
<some-HTML-element some-event=“JavaScript 代码”>
~~~

| 事件        | 描述                         |
| :---------- | :--------------------------- |
| onchange    | HTML 元素改变                |
| onclick     | 用户点击 HTML 元素           |
| onmouseover | 用户在一个HTML元素上移动鼠标 |
| onmouseout  | 用户从一个HTML元素上移开鼠标 |
| onkeydown   | 用户按下键盘按键             |
| onload      | 浏览器已完成页面的加载       |

## 9.break 和 continue 语句

> 1. break 语句可用于跳出循环。
> 2. **continue 语句**中断循环中的迭代，如果出现了指定的条件，然后继续循环中的下一个迭代。

## 10.错误-throw、try、catch

> 1. **try** 语句测试代码块的错误
> 2. **catch** 语句处理错误
> 3. **throw** 语句创建自定义错误
> 4. **finally** 语句在 try 和 catch 语句之后，无论是否有触发异常，该语句都会执行

~~~js
try{
    ... //异常的抛出
    throw 
}catch(e){
    ... //异常的捕获与处理
}finally{
    ... //结束处理
}
~~~

## 11.变量提升

> 1. 函数及变量的声明都将被提升到函数的最顶部
> 2. 变量可以在使用后声明，也就是变量可以先使用再声明
> 3. 只有声明的变量会提升，初始化的不会
> 4. 建议在作用域开始前声明变量



## 12.严格模式（use strict）

> 严格模式下未声明的变量不能使用
>
> - 消除代码运行的一些不安全之处，保证代码运行的安全；
> - 提高编译器效率，增加运行速度；
> - 为未来新版本的Javascript做好铺垫。



## 13.this关键字

> this 表示当前对象的一个引用

- 在方法中，this 表示该方法所属的对象。
- 如果单独使用，this 表示全局对象。
- 在函数中，this 表示全局对象。
- 在函数中，在严格模式下，this 是未定义的(undefined)。
- 在事件中，this 表示接收事件的元素。
- 类似 call() 和 apply() 方法可以将 this 引用到任何对象。

~~~js
var person1 = {
  fullName: function() {
    return this.firstName + " " + this.lastName;
  }
}
var person2 = {
  firstName:"John",
  lastName: "Doe",
}
person1.fullName.call(person2);  // 返回 "John Doe"
~~~

## 14.let和const

> let 声明的变量只在 let 命令所在的代码块内有效
>
> const 声明一个只读的常量，一旦声明，常量的值就不能改变

~~~js
var x = 10;
// 这里输出 x 为 10
{ 
    let x = 2;
    // 这里输出 x 为 2
}
// 这里输出 x 为 10
~~~

> `const`定义常量与使用`let` 定义的变量相似：
>
> - 二者都是块级作用域
> - 都不能和它所在作用域内的其他变量或函数拥有相同的名称
>
> 两者还有以下两点区别：
>
> - `const`声明的常量必须初始化，而`let`声明的变量不用
> - const 定义常量的值不能通过再赋值修改，也不能再次声明。而 let 定义的变量值可以修改。

## 15.JSON

> 用于存储和传输数据的格式,通常用于服务端向网页传递数据 

~~~json
//JavaScript Object Notation
{"sites":[
    {"name":"Runoob", "url":"www.runoob.com"}, 
    {"name":"Google", "url":"www.google.com"},
    {"name":"Taobao", "url":"www.taobao.com"}
]}
~~~

- 数据为 键/值 对
- 数据由逗号分隔
- 大括号保存对象
- 方括号保存数组

> 1. JSON.parse()      将JSON转换未JavaScript对象
> 2. JSON.stringify()  将JavaScript对象转换未JSON

## 16.闭包

> 是它可以访问函数上一层作用域的计数器。这个叫作 JavaScript **闭包。**它使得函数拥有私有变量变成可能。

> 闭包是一种保护私有变量的机制，在函数执行时形成私有的作用域，保护里面的私有变量不受外界干扰。直观的说就是形成一个不销毁的栈环境。

~~~js
var add = (function () {
    var counter = 0;
    return function () {return counter += 1;}
})();
~~~

![preview](https://pic2.zhimg.com/v2-bfc369d7c79b62ce8f3034fe1d0dc66a_r.jpg?source=1940ef5c)

~~~js
function f(b) {
  return function g(c) {
    return function h(d) {
      return a + b + c + d
    }
  }
}

var add2 = f(2)

var add4 = add2(2)
var add5 = add2(3)

var r1 = add4(10)
var r2 = add5(10)

console.log(r1,r2) //14,15
~~~

## 17.HTML DOM

> HTML DOM 树

![DOM HTML tree](https://www.runoob.com/images/pic_htmltree.gif)

- JavaScript 能够改变页面中的所有 HTML 元素
- JavaScript 能够改变页面中的所有 HTML 属性
- JavaScript 能够改变页面中的所有 CSS 样式
- JavaScript 能够对页面中的所有事件做出反应

### 17.1 查找HTML元素

> gitElementById
>
> gitElementByClassName
>
> gitElementByTagName

### 17.2 改变HTML内容

> 更改元素的内容  innerHTML
>
> 更改元素的属性 （document.getElementById(*id*).*attribute=新属性值*）

### 17.3改变CSS

> document.getElementById(id).style.property = 新样式

### 17.4 HTML DOM事件

- 当用户点击鼠标时    onclick
- 当网页已加载时    onload 
- 当图像已加载时
- 当鼠标移动到元素上时 onmouseover、onmouseout
- 当输入字段被改变时 onchange 
- 当提交 HTML 表单时
- 当用户触发按键时

### 17.5 HTML DOM EventListener

> addEventListener() 方法用于向指定元素添加事件句柄

~~~js
element.addEventListener(event, function, useCapture);
//event如：click等
//fucntion:触发后调用的函数
//useCapture:布尔值用于描述事件是冒泡还是捕获
element.removeEventListener("mousemove", myFunction);
~~~

> 事件冒泡或事件捕获
>
> 事件传递有两种方式 : 冒泡与捕获。事件传递定义了元素触发的顺序。
>
> 冒泡：内部元素的事件会先被触发
>
> 捕获：外部元素事件先被触发

### 17.6 HTML DOM 元素（节点）

> appendChild():添加元素到尾部  insertBefore():添加新元素到尾部
>
> createElement:创建元素
>
> createTextNode：创建文本节点
>
> removeChild:移除已存在的元素
>
> replaceChild：替换html中的元素

## 18.对象

> JavaScripty中的所有事物都是对象
>
> 对象只是一种特殊的数据，对象拥有属性和方法

~~~js
//使用 Object 定义并创建对象的实例
var o = new object();
//使用函数来定义对象，然后创建新的对象实例
function person(firstname,lastname,age,eyecolor)
{
    this.firstname=firstname;
    this.lastname=lastname;
    this.age=age;
    this.eyecolor=eyecolor;
}

~~~

### 18.1 原型对象（prototype）

> 所有对象都会从一个 prototype（原型对象）中继承属性和方法

- `Date` 对象从 `Date.prototype` 继承。
- `Array` 对象从 `Array.prototype` 继承。
- `Person` 对象从 `Person.prototype` 继承。

> JavaScript 对象有一个指向一个原型对象的链。当试图访问一个对象的属性时，它不仅仅在该对象上搜寻，还会搜寻该对象的原型，以及该对象的原型的原型，依次层层向上搜索，直到找到一个名字匹配的属性或到达原型链的末尾。

> **构造函数名.prototype.新属性或者新方法**

### 18.2 Number 对象

> js数字不分整数和浮点类型，都是属于浮点类型

> 因为有精度问题，所以在电商计算的时候都是换算成分来计算

## 19.浏览器BOM

### 19.1 window -浏览器对象模型

> 浏览器对象：浏览器窗口

### 19.2 Window Screen

> 有关用户的屏幕信息
>
> screen.availWidth-可用屏幕宽度
>
> screen.availHeight-可用屏幕高度

### 19.3 Window Location

> window.location 对象用于获得当前页面的地址 (URL)，并把浏览器重定向到新的页面

- location.hostname 返回 web 主机的域名
- location.pathname 返回当前页面的路径和文件名
- location.port 返回 web 主机的端口 （80 或 443）
- location.protocol 返回所使用的 web 协议（http: 或 https:）

### 19.4 Window History

> 包含浏览器的历史

~~~JS
//与在浏览器点击后退按钮相同效果
history.back();
//与在浏览器中点击前进按钮相同效果
history.forward();

~~~

### 19.5 Window Navigator

~~~js
txt = "<p>浏览器代号: " + navigator.appCodeName + "</p>";
txt+= "<p>浏览器名称: " + navigator.appName + "</p>";
txt+= "<p>浏览器版本: " + navigator.appVersion + "</p>";
txt+= "<p>启用Cookies: " + navigator.cookieEnabled + "</p>";
txt+= "<p>硬件平台: " + navigator.platform + "</p>";
txt+= "<p>用户代理: " + navigator.userAgent + "</p>";
txt+= "<p>用户代理语言: " + navigator.language + "</p>";
~~~

> 来自 navigator 对象的信息具有误导性，不应该被用于检测浏览器版本

~~~js
//不同的浏览器支持不同的对象，您可以使用对象来检测浏览器
if (window.opera) {...some action...}
~~~

### 19.6 弹窗

> 三种消息框：警告框、确认框、提示框

~~~js
window.alert();

var r=confirm("按下按钮");
if (r==true){
    x="你按下了\"确定\"按钮!";
}else{
    x="你按下了\"取消\"按钮!";
}

window.prompt("sometext","defaultvalue");
~~~

### 19.7计时事件

- setInterval() - 间隔指定的毫秒数不停地执行指定的代码。
- setTimeout() - 在指定的毫秒数后执行指定代码。

### 19.8 Cookie

~~~js
document.cookie="username=John Doe; expires=Thu, 18 Dec 2043 12:00:00 GMT";
~~~

##  20.JavaScripty 库

> jquery...