# css学习

## 1.什么是CSS

> css是层叠样式表

## 2.CSS语法

![632877C9-2462-41D6-BD0E-F7317E4C42AC.jpg](https://i.loli.net/2021/02/24/txhPKl2ENRBY14m.jpg)

## 3.id和class选择器

~~~css
#id{color:red}
.class{color:blue}
/*
*1.id选择器只能再一个元素中使用，class选择器可以在多个元素中使用
*1.不要以数字开头，在部分浏览器不起作用
*/
~~~

## 4.CSS的引入

~~~html
<head>
    <!--外部样式表-->
	<link rel="stylesheet" type="text/css" href="mystyle.css">
    <!--内部样式表-->
	<style>
        p {margin-left:20px;}
	</style>
</head>
<!--内联样式表-->
<p style="color:sienna;margin-left:20px">这是一个段落。</p>
<!--
(内联样式）Inline style > （内部样式）Internal style sheet >（外部样式）External style sheet > 浏览器默认样式
注意：如果外部样式放在内部样式的后面，则外部样式将覆盖内部样式。
-->
~~~

## 5.CSS各种属性

## 6.盒子模型

> - **Margin(外边距)** - 清除边框外的区域，外边距是透明的。
> - **Border(边框)** - 围绕在内边距和内容外的边框。
> - **Padding(内边距)** - 清除内容周围的区域，内边距是透明的。
> - **Content(内容)** - 盒子的内容，显示文本和图像。

![box-model.gif](https://i.loli.net/2021/02/24/1vecHFQOjD624sT.gif)

## 7.CSS Position 定位

>- static 定位 默认值。即没有定位
>- fixed 定位 相对于浏览器窗口固定位置
>- relative 定位 相对定位元素的定位是其相对正常位置
>- absolute 定位 绝对定位的位置相对于最近的已定位的父元素，如没已定位的父元素则相对于<html>
>- sticky 定位 粘性定位基于用户滚动位置进行定位

## 8.CSS Float 浮动

> CSS浮动会使元素向左或向右移动，其周围的元素也会重新排列

## 9.CSS Media 媒体查询

> 媒体类型允许你指定文件将如何在不同媒体呈现。该文件可以以不同的方式显示在屏幕上，在纸张上，或听觉浏览器等等。

~~~css
/* 响应式布局 layout - 在屏幕宽度小于 600px 时， 设置为上下堆叠元素 */
@media screen and (max-width: 600px) {
  .col-25, .col-75, input[type=submit] {
    width: 100%;
    margin-top: 0;
  }
}
~~~

## 10.flex 弹性布局

[相关文章](http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html)

## 11.grid格栅布局

[相关文章](http://www.ruanyifeng.com/blog/2019/03/grid-layout-tutorial.html)





