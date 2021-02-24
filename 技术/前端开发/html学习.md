# HTML学习

## 学习HTML基础

### HTML是什么？

> HyperText Markup Language(超文本标记语言) 是一种用于创建网页的标准标记语言

### HTML标题

```	html
<h1>这是一个标题</h1>
<h2>这是一个标题</h2>
<h3>这是一个标题</h3>
...
```

### HTML段落

~~~html
<p>这是一个段落。</p>
<p>这是另外一个段落。</p>
~~~

### HTML链接

~~~html
<a href="https://www.google.com">这是一个链接</a>
~~~

### HTML图像

~~~html
<img loading="lazy" src="/images/logo.png" width="258" height="39" alt="Big Boat" />
~~~

### HTML head元素

~~~html

<title> <!--定义了标题-->
<base>  <!--定义了页面链接的默认地址-->
<link>  <!--定义了一个文档和外部资源之间的关系-->
<meta>  <!--定义了HTML文档中的元数据-->
<style> <!--定义了客户端的脚本文件-->
<script> <!--定义了HTML文档的样式文件-->
     
~~~

### HTML table

~~~html
<table border="1">
    <tr>
        <th>Header 1</th>
        <th>Header 2</th>
    </tr>
    <tr>
        <td>row 1, cell 1</td>
        <td>row 1, cell 2</td>
    </tr>
    <tr>
        <td>row 2, cell 1</td>
        <td>row 2, cell 2</td>
    </tr>
</table>
~~~

### HTML 列表

~~~html
<ul>
    <li></li>
    <ol></ol>
</ul>
<dl>
    <dt></dt>
    <dd></dd>
</dl>
~~~

### HTML 区块元素

~~~html
<!--区块元素-->
<h1>,<p>,<ul>,<table>,<div>
<!--内联元素-->
<b><td><a><img><span>

~~~



### HTML CSS

- 内联样式- 在HTML元素中使用"style" **属性**
- 内部样式表 -在HTML文档头部 <head> 区域使用<style> **元素** 来包含CSS
- 外部引用 - 使用外部 CSS **文件**

### HTML文本格式化标签

~~~html
<b>粗体文字</b>
<em>着重文字</em>
<i>斜体字</i>
<small>小号字</small>
<strong>加重</strong>
<sub>下标字</sub>
<sup>上标字</sup>
<ins>插入字</ins>
<del>删除字</del>
~~~

~~~html
<code>计算机代码</code>
<kbd>键盘码</kbd>
<samp>计算机代码样本</samp>
<var>变量</var>
<pre>预格式文本</pre>
~~~

~~~html
<abbr>缩写</abbr>
<address>地址</address>
<bdo>文字方向</bdo>
<blockquoto>长引用</blockquoto>
<q>短引用</q>
<cite>引用/引证</cite>
<dfn>项目</dfn>
~~~



### HTML元素语法

- HTML 元素以**开始标签**起始
- HTML 元素以**结束标签**终止
- **元素的内容**是开始标签与结束标签之间的内容
- 某些 HTML 元素具有**空内容（empty content）**
- 空元素**在开始标签中进行关闭**（以开始标签的结束而结束）
- 大多数 HTML 元素可拥有**属性**
- 推荐不要忘记关闭标签+使用小写标签

### HTML属性

- HTML 元素可以设置**属性**
- 属性可以在元素中添加**附加信息**
- 属性一般描述于**开始标签**
- 属性总是以名称/值对的形式出现，**比如：name="value"**

### HTML布局

> div 定义文档区块，块级
>
> span 用来组合文档中的行内元素

### HTML 表单

~~~html
<form>
    <!--文本字段-->
    <input type="text" name="xxx"/>
    <!--密码字段-->
    <input type="password" name="xxx"/>
    <!--单选按钮-->
    <input type="radio" name="sex" value="male"/>
    <input type="radio" name="sex" value="female"/>
    <!--复选按钮-->
	<input type="checkbox" name="num" value="1"/>
	<input type="checkbox" name="num" value="2"/>
    <!--提交按钮-->
    <input type="submit" value="Submit">
    <!--选择下拉-->
    <select name="cars">
        <option value="volvo">Volvo</option>
        <option value="saab">Saab</option>
    </select> 
</form>
~~~

### HTML框架

~~~html
<iframe src="" width='200' height='200' frameborder='0'></iframe>
~~~

### HTML5 

> HTML5是一种HTML标准

- 用于绘画的 canvas 元素
- 用于媒介回放的 video 和 audio 元素
- 对本地离线存储的更好的支持
- 新的特殊内容元素，比如 article、footer、header、nav、section
- 新的表单控件，比如 calendar、date、time、email、url、search

## 书写语义化的HTML

> HTML5 定了 8 个新的 HTML **语义（semantic）** 元素。所有这些元素都是 **块级** 元素

~~~css
#兼容旧版本浏览器
header, section, footer, aside, nav, main, article, figure {
    display: block; 
}
<!--[if lt IE 9]>
  <script src="http://html5shiv.googlecode.com/svn/trunk/html5.js"></script>
  <script src="http://cdn.static.runoob.com/libs/html5shiv/3.7/html5shiv.min.js"></script>
<![endif]-->
~~~

![18cd04ac-b58a-4c19-8455-430344c30ed9.jpg](https://i.loli.net/2021/02/23/3G61yuBnStH7Ebj.jpg)

## 表单和验证



## 惯例和最佳实践

