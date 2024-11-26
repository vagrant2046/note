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
			- 是一个用于传输超媒体文档（例如 HTML）的[应用层]协议
			- Web浏览器与Web服务器之间通信而设计的
			- 客户端-服务端模型
			- 无状态协议，服务器不会再两个请求之间保留任何数据（状态）
		- HTTP能控制什么
			- 缓存
			- 开放同源限制
			- 认证
			- 代理服务器和隧道
			- 会话
		- HTTP流
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
			- ![http.png](../assets/http_1731895549028_0.png){:height 253, :width 357}
			- HTTP方法
				- GET、POST
			- 要获取的那个资源的路径
			- HTTP 协议版本号
			- 为服务端表达其他信息的可选标头
			- 请求体（body），类似于响应中的请求体，一些像 `POST` 这样的方法，请求体内包含需要了发送的资源。
		- HTTP响应
			- ![respond.png](../assets/respond_1731895736221_0.png){:height 231, :width 451}
			- HTTP 协议版本号
			- 状态码
			- 状态信息
			- HTTP标头
			- 可选项
		- HTTP状态码
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
-