# Css-Flex布局学习

## 1.Flex布局是什么

> Flex 是 Flexible Box 的缩写，意为"弹性布局"，用来为盒状模型提供最大的灵活性

## 2.Flex基本用法

~~~css
.box{
    display:flex;
    display:-webkit-flex; /* Safari */
}
~~~

> 1. 采用flex布局得元素。成为Flex容器（flex container）
> 2. 它的所有子元素自动成为容器成员,称为 Flex 项目（flex item）
> 3. 容器默认存在两根轴：水平的主轴（main axis）和垂直的交叉轴（cross axis）

![img](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071004.png)

## 3.容器的属性

~~~css
.box{
    flex-flow: <flex-direction> || <flex-wrap>;
    /*
    * flex-direction 决定主轴的方向（即项目的排列方向）
    * flex-direction: row | row-reverse | column | column-reverse;
    * flex-wrap 决定一条轴线拍不下，如何换行
    * flex-wrap: nowrap | wrap | wrap-reverse;
    */
}

.box {
  justify-content: flex-start | flex-end | center | space-between | space-around;
  /*
   * justify-content 属性定义了项目在主轴上的对齐方式
   * space-between：两端对齐，项目之间的间隔都相等
   * space-around：每个项目两侧的间隔相等。所以，项目之间的间隔比项目与边框的间隔大一倍
  */
}

.box {
  align-items: flex-start | flex-end | center | baseline | stretch;
  align-content: flex-start | flex-end | center | space-between | space-around | stretch;
  /*
   * 都是定义项目在交叉轴上如何对齐,但是align-content只对多行的flex容器起作用
   * baseline 项目的第一行文字的基线对齐
   * stretch 如果项目未设置高度或设为auto，将占满整个容器的高度
   *
  */
}


~~~

## 4.项目属性

~~~css
.item {
  order: <integer>;
  /*定义项目的顺序，数值越小，排列越靠前*/
}

.item {
  flex: none | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'> ]
}
.item {
  flex-grow: <number>; /* default 0 */
  /*定义项目的放大比例*/
}
.item {
  flex-shrink: <number>; /* default 1 */
  /*定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小*/
}
.item {
  flex-basis: <length> | auto; /* default auto */
  /*定义了在分配多余空间之前，项目占据的主轴空间（main size）*/
}
.item {
  align-self: auto | flex-start | flex-end | center | baseline | stretch;
  /*align-self属性允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性*/
}
~~~

## 项目实战

[参考](http://www.ruanyifeng.com/blog/2015/07/flex-examples.html)