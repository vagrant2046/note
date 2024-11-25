- 1.**[How Internet & Websites works](https://github.com/thecodeholic/php-developer-roadmap#how-internet--websites-works)**
  collapsed:: true
	- How does the INTERNET work?
		- 9m https://www.youtube.com/watch?v=x3c1ih2NJEg
	- How The Web Works - The Big Picture
		- 12m https://www.youtube.com/watch?v=hJHvdBlSxug
	- How does the internet work? (Full Course)
		- 1h 42m
		- [https://youtu.be/zN8YNNHcaZc](https://youtu.be/zN8YNNHcaZc)
	- https://roadmap.sh/guides/what-is-internet
		- 什么是互联网？
		  collapsed:: true
			- 互相连接的计算机组成的全球网络
			- 通过标准化的协议进行通信
		- 信息如何在互联网上传输？
		  collapsed:: true
			- Internet 上的信息通过各种介质（包括以太网电缆、光纤电缆和无线信号（即无线电波））以比特的形式从一台计算机移动到另一台计算机。
		- 网络如何互相通信，以及其中的协议？
			- IP
				- 电脑的网络地址标识符
			- 域名
				- IP的别名
			- DNS
				- IP和域名的映射表
			-
		- 数据包、路由器和可靠性之间有什么关系？
		  collapsed:: true
			- 数据包
				- 网络上传输的数据包不需要遵循固定路径
				- 数据包可以分成多个小包按不同路径抵达目的地
			- 路由器
				- 包的中转站，控制包的路径选择以及检查包的完整性安全性
			- 可靠性
				- 通过TCP协议保证传输的可靠性
		- HTTP 和 HTML – 您如何在浏览器中查看此网页？
			- ![网页如何看到的](../assets/1111_1731565910603_0.png){:height 373, :width 592}
		- 互联网上的信息传输如何确保安全？
			- ssl、tls
			- 非对称加密
		- 什么是网络安全，有哪些常见的互联网犯罪？
			- 网络安全是指通过使用网络、技术设备和互联网实现的针对犯罪活动的保护措施
- 2.**[Browser/Server request flow, HTTP Protocol, Status codes](https://github.com/thecodeholic/php-developer-roadmap#browserserver-request-flow-http-protocol-status-codes)**
  collapsed:: true
	- HTTP Crash Course & Exploration
		- https://www.youtube.com/watch?v=iYM2zFP3Zn0
		- https://developer.mozilla.org/zh-CN/docs/Web/HTTP
		- HTTP(超文本传输协议)
		  collapsed:: true
			- 是一个用于传输超媒体文档（例如 HTML）的[应用层]协议
			- Web浏览器与Web服务器之间通信而设计的
			- 客户端-服务端模型
			- 无状态协议，服务器不会再两个请求之间保留任何数据（状态）
		- HTTP能控制什么
		  collapsed:: true
			- 缓存
			- 开放同源限制
			- 认证
			- 代理服务器和隧道
			- 会话
		- HTTP流
		  collapsed:: true
			- 1.打开一个 TCP 连接
				- TCP 连接被用来发送一条或多条请求，以及接受响应消息。
			- 2.发送一个 HTTP 报文
				- ```http
				  GET / HTTP/1.1
				  Host: developer.mozilla.org
				  Accept-Language: zh
				  ```
			- 3.读取服务端返回的报文信息
				- ```http
				  HTTP/1.1 200 OK
				  Date: Sat, 09 Oct 2010 14:28:02 GMT
				  Server: Apache
				  Last-Modified: Tue, 01 Dec 2009 20:18:22 GMT
				  ETag: "51142bc1-7449-479b075b2891b"
				  Accept-Ranges: bytes
				  Content-Length: 29769
				  Content-Type: text/html
				  
				  <!DOCTYPE html>…（此处是所请求网页的 29769 字节）
				  ```
			- 4.关闭连接或者为后续请求重用连接
		- HTTP报文
		  collapsed:: true
			- ![http.png](../assets/http_1731895549028_0.png){:height 253, :width 357}
			- HTTP方法
				- GET、POST
			- 要获取的那个资源的路径
			- HTTP 协议版本号
			- 为服务端表达其他信息的可选标头
			- 请求体（body），类似于响应中的请求体，一些像 `POST` 这样的方法，请求体内包含需要了发送的资源。
		- HTTP响应
		  collapsed:: true
			- ![respond.png](../assets/respond_1731895736221_0.png){:height 231, :width 451}
			- HTTP 协议版本号
			- 状态码
			- 状态信息
			- HTTP标头
			- 可选项
		- HTTP状态码
		  collapsed:: true
			- *1xx 信息性响应* – 请求已接收，正在继续处理
			- *2xx 成功* – 请求已成功接收、理解并接受
			- *3xx 重定向* – 需要采取进一步的措施以完成请求
			- *4xx 客户端错误* – 请求包含语法错误或无法完成
			- *5xx 服务器错误* – 服务器未能完成明显有效的请求
			- **200 OK**
				- 请求已成功，请求所希望的响应头或数据体将随此响应返回。
			- **201 Created**
				- 请求已经被实现，而且有一个新的资源已经依据请求的需要而建立，且其[URI](https://zh.wikipedia.org/wiki/URI)已经随Location头信息返回。
			- **301 Moved Permanently**
				- 被请求的资源已永久移动到新位置，并且将来任何对此资源的引用都应该使用本响应返回的若干个URI之一
			- **301 Found**
				- 要求客户端执行临时重定向，由于这样的重定向是临时的，客户端应当继续向原有地址发送以后的请求。
			- **403 Forbidden**
				- 请求失败，请求所希望得到的资源未被在服务器上发现，但允许用户的后续请求。
			- **404 Not Found**
				- 请求失败，请求所希望得到的资源未被在服务器上发现，但允许用户的后续请求。
			- **401 Unauthorized**
				- 未认证
			- **500 Internal Server Error**
			- **502 Bad Gateway**
- 3. Basics of HTML/CSS
	- HTML
	  collapsed:: true
		- 1.什么是HTML
		  collapsed:: true
			- 超文本标记语言
		- 2.什么是HTML Element（元素）
		  collapsed:: true
			- HTML **元素**是从 start 标签到 end 标签的所有内容
		- 3.HTML  Basic
		  collapsed:: true
			- 1.必须声明文档类型`<!DOCTYPE html>`
			- 2.开始于 `<html>`结束于`</html>`
			- 3.`<body>` 和`</body>`之间存放可见部分
			  collapsed:: true
				- ```html
				  <!DOCTYPE html>
				  <html>
				    <body>
				    </body>
				  </html>
				  ```
			- 4.HTML 标题
			  collapsed:: true
				- `<h1>`-`<h6>`
				- `<h1>` 定义最重要的标题。`<h6>` 定义最不重要的标题
			- 5.HTML 段落
			  collapsed:: true
				- `<p>`
			- 6.HTML 链接
			  collapsed:: true
				- `<a>`
				  collapsed:: true
					- _self
					- _blank
					- _parent
					- _top
				- 页面bookmark
					- ```html
					  <h2 id="C4">Chapter 4</h2>
					  <a href="#C4">Jump to Chapter 4</a>
					  ```
			- 7.HTML 图像
			  collapsed:: true
				- `<img>`
				- 源文件 （`src`）、替代文本 （`alt`）、`width` 和 `height` 作为属性提供
			- 8.HTML 水平线
			  collapsed:: true
				- `<hr>`
			- 9.HTML 换行符
			  collapsed:: true
				- `<br>`
			- 10.HTML预格式化文本
			  collapsed:: true
				- `<pre>`
			- 11.Image Maps
			  collapsed:: true
				- ```html
				  <img src="workplace.jpg" alt="Workplace" usemap="#workmap">
				  <map name="workmap">
				    <area shape="rect" coords="34,44,270,350" alt="Computer" href="computer.htm">
				    <area shape="rect" coords="290,172,333,250" alt="Phone" href="phone.htm">
				    <area shape="circle" coords="337,300,44" alt="Coffee" href="coffee.htm">
				  </map>
				  ```
			- collapsed:: true
			  12. <picture>
				- `<picture>` 元素允许您为不同的设备或屏幕大小显示不同的图片
				- ```html
				  <picture>
				    <source media="(min-width: 650px)" srcset="img_food.jpg">
				    <source media="(min-width: 465px)" srcset="img_car.jpg">
				    <img src="img_girl.jpg">
				  </picture>
				  ```
			- 13.favicon
			  collapsed:: true
				- ```html
				  <link rel="icon" type="image/x-icon" href="/images/favicon.ico">
				  ```
			- 14.HTML Title
			  collapsed:: true
				- `<title>`
		- 4.HTML 属性
		  collapsed:: true
			- 属性提供HTML元素的附加信息，所有 HTML 元素都可以具有**属性**
			- `href` 属性指定链接指向的页面的 URL
			- `src` 属性指定要显示的图像的路径
			- `style` 属性用于向元素添加样式，例如颜色、字体、大小等
			- `title` 属性定义有关元素的一些额外信息
		- 5.HTML 样式
		  collapsed:: true
			- HTML `style` 属性用于向元素添加样式，例如颜色、字体、大小等
			- `<tagname  style="property:value;">`
		- 6.HTML 文本格式
		  collapsed:: true
			- `<b>` - 粗体文本不带重要性
			- `<strong>` - 重要文本
			- `<i>` - 斜体文本
			- `<em>` - 强调的文本
			- `<mark>` - 已标记的文本
			- `<small>` - 文本较小
			- `<del>` - 已删除文本
			- `<ins>` - 插入的文本
			- `<sub>` - 下标文本
			- `<sup>` - 上标文本
		- 7.HTML 引用
		  collapsed:: true
			- `<blockquote>` 元素定义从其他来源引用的章节
			- `<q>` 标记定义简短的引用，加引号
			- `<abbr>` 标签定义缩写或首字母缩略词
			- `<address>` 标签定义文档或文章的作者/所有者的联系信息
			- `<cite>` 标签定义了创意作品的标题
			- `<bdo>` 标签用于覆盖当前文本方向
		- 8.HTML 注释
		  collapsed:: true
			- ```html
			  <!-- Write your comments here -->
			  ```
		- 9.HTML 颜色
		  id:: 6743ca50-bb7a-4007-b0d5-008605482356
		  collapsed:: true
			- RGB
				- `rgb(255, 99, 71)`
			- HEX
				- `#ff6347`
			- HSL
				- `hsl(9, 100%, 64%)`
		- 10.HTML CSS
		  collapsed:: true
			- **内联** - 通过在 HTML 元素中使用 `style` 属性
			- **内部** - 通过在 `<head> 部分中使用 <style>` 元素
			- **外部** - 通过使用 `<link>` 元素链接到外部 CSS 文件
		- 11.HTML Tables
		  collapsed:: true
			- `<td>`
				- Table Cells
			- `<tr>`
				- Table rows
			- `<th>`
				- Table Headers
			- `:nth-child(even)`
				- ```css
				  tr:nth-child(even) {
				    background-color: #D6EEEE;
				  }
				  ```
		- 12.HTML Lists
		  collapsed:: true
			- `<ul>`
				- 无序列表
			- `<ol>`
				- 有序列表
			- `<dl>`
				- 描述列表
		- 13.HTML Block and Inline Elements
		  collapsed:: true
			- block
				- `<p>`、`<div>`、`<nav>`...
			- inline
				- `<span>`、`<a>`...
		- 14.HTML  DIV\CLASS\ID
		  collapsed:: true
			- `<div>`、`<div class="classname">`、`<div id="idname">`
		- 15.HTML Iframes
		  collapsed:: true
			- ```html
			  <iframe src="url" title="description"></iframe>
			  ```
		- 16.HTML Responsive Web Design
		  collapsed:: true
			- Setting The Viewport
			  collapsed:: true
				- ```html
				  <meta name="viewport" content="width=device-width, initial-scale=1.0">
				  ```
			- css width
			  collapsed:: true
				- ```html
				  <img src="img_girl.jpg" style="width:100%;">
				  ```
			- <picture>
			- `vw`、`vh`
			- Media Queries
			  collapsed:: true
				- ```CSS
				  /* The width is 100%, when the viewport is 800px or smaller */
				  @media screen and (max-width: 800px) {
				    .left, .main, .right {
				      width: 100%; 
				    }
				  }
				  ```
			- Framework
				- Bootstrap...
		- 17.语义化HTML
		  collapsed:: true
			- `<header>` - 定义文档或章节的页眉
			- `<nav>` - 定义一组导航链接
			- `<section>` - 定义文档中的节
			- `<article>` - 定义独立的自包含内容
			- `<aside>` - 定义内容以外的内容（如侧边栏）
			- `<footer>` - 定义文档或部分的页脚
			- `<details>` - 定义用户可按需打开和关闭的其他详细信息
			- `<summary>` - 定义 `<details>` 元素的标题
			- ![img_sem_elements.gif](../assets/img_sem_elements_1732256896806_0.gif)
		- 18.HTML 样式指导
		  collapsed:: true
			- 1.始终将文档类型声明为文档中的第一行
			- 2.使用小写元素名称
			- 3.关闭所有 HTML 元素
			- 4.使用小写属性名称
			- 5.始终引用属性值
			- 6.始终为图像指定 `alt` 属性
		- 19.HTML 实体符号
		  collapsed:: true
			- `空格`-`&nbsp;`
			- `<` - `&lt;`
			- `>` - `&gt;`
			- `©` - `&copy;`
		- 20.HTML charset
		  collapsed:: true
			- ```html
			  <meta charset="UTF-8">
			  ```
		- 21.HTML URL ENCODE
		  collapsed:: true
			- url在地址栏里面经过编码
		- 22.HTML Forms
		  collapsed:: true
			- `<form>`
			  collapsed:: true
				- `action`
				- `method`
				- `autocomplete`
			- <form> elements
			  collapsed:: true
				- `<input>`
				- `<label>`
				- `<select>`
				- `<textarea>`
				- `<button>`
				- `<fieldset>`
				- `<legend>`
				- `<datalist>`
					- 预定于选项
				- `<output>`
				- `<option>`
				- `<optgroup>`
			- input type
				- `<input type="button">`
				- `<input type="checkbox">`
				- `<input type="color">`
				- `<input type="date">`
				- `<input type="datetime-local">`
				- `<input type="email">`
				- `<input type="file">`
				- `<input type="hidden">`
				- `<input type="image">`
				- `<input type="month">`
				- `<input type="number">`
				- `<input type="password">`
				- `<input type="radio">`
				- `<input type="range">`
				- `<input type="reset">`
				- `<input type="search">`
				- `<input type="submit">`
				- `<input type="tel">`
				- `<input type="text">`
				- `<input type="time">`
				- `<input type="url">`
				- `<input type="week">`
			-
	- CSS
		- 1.CSS describes how HTML elements should be displayed
		- 2.基本语法
		  collapsed:: true
			- ![微信截图_20241125102833.jpg](../assets/微信截图_20241125102833_1732501735847_0.jpg)
		- 3.选择器
		  collapsed:: true
			- 1.简单选择器
			  collapsed:: true
				- 元素名称
				- id选择器
					- id在页面内是唯一的
				- class
				- 通用选择期
					- ```css
					  *{
					    test-align:center;
					  }
					  ```
				- 分组选择器
					- ```css
					  h1, h2, p{
					    color:res;
					  }
					  ```
			- 2.组合选择器
			  collapsed:: true
				- 元素之间特定关系
			- 3.伪类选择器
			  collapsed:: true
				- 根据某种状态
			- 4.伪元素选择器
			  collapsed:: true
				- 选择元素的一部分并为其设置样式
		- 4.添加CSS方式
		  collapsed:: true
			- 外部css
			  collapsed:: true
				- ```html
				  <link rel="stylesheet" href="mystyle.css">
				  ```
			- 内部css
			  collapsed:: true
				- ```html
				  <style>
				    body{
				      background:red;
				    }
				  </style>
				  ```
			- 内联css
			  collapsed:: true
				- ```html
				  <p style="color:red;">This is a paragraph.</p>
				  ```
			- 级联顺序
			  collapsed:: true
				- 内联css具有最高优先权
				- 内部css和外部css按页面加载最后面的优先权越高
		- 5.CSS注释
		  collapsed:: true
			- ```css
			  /*this is a signle-line comment*/
			  p {
			    color:red;
			  }
			  ```
		- 6.CSS颜色
		  collapsed:: true
			- {{embed ((6743ca50-bb7a-4007-b0d5-008605482356))}}
			-
		- 7.CSS背景
		  collapsed:: true
			- ```css
			  body {
			     background: #ffffff url("img_tree.png") no-repeat fix top;
			  }
			  /*
			  * background-color
			  * background-image
			  * background-repeat
			  * background-attachment  属性指定背景图像是否应该滚动或固定
			  * background-position
			  */
			  ```
		- 8.CSS边框
		  collapsed:: true
			- ```css
			  p {
			    border：5px solid red;
			    border-radius: 5px;
			  }
			  ```
		- 9.CSS边距
		  collapsed:: true
			- ```css
			  p {
			    margin: 10px 11px 12px 9px;
			    /* 上 右 下 左 */
			  }
			  ```
			- Margin Collapse
				- ```css
				  h1 {
				    margin: 0 0 50px 0;
				  }
				  h2 {
				    margin: 20px 0 0 0;
				  }
				  /*
				  *常识似乎表明 <h1> 和 <h2> 之间的垂直边距总计为 70px (50px + 20px)
				  *但由于边距塌陷，实际边距最终为 50px
				  */
				  ```
		- 10.CSS填充
		  collapsed:: true
			- ```css
			  div {
			    padding: 25px 50px 75px 100px;/*上右下左*/
			  }
			  /*padding 占据宽度，可以使用box-sizing*/
			  div {
			    width:300px;
			    padding:25px;
			    box-sizing:border-box;
			  }
			  ```
		- 11.CSS   Height, Width and Max-width
		- 12.CSS盒子模型
		  background-color:: red
		  collapsed:: true
			- ![微信截图_20241125133344.jpg](../assets/微信截图_20241125133344_1732512848222_0.jpg){:height 233, :width 687}
		- 13.CSS outline
		- 14.CSS 文本
		  collapsed:: true
			- `color`
			- `text-align`、`text-align-last`
			- `direction`
			- `vertical-align`
			- `text-decoration: none;`
			- `text-transform`
			  collapsed:: true
				- 文本字母大小写转换
			- `text-indent`           文本缩进
			- `letter-spacing`   字母间距
			- `line-height` 行高
			- `word-spacing` 字间距
			- `white-space` 文本换行
			- `text-shadow`文本阴影
			-
		- 15.CSS 字体
	-
	-
-
-
-