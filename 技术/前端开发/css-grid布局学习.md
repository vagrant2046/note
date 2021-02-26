# css-grid布局学习

## 1.什么交Grid布局

> 1. 可以指定容器内部多个项目的位置
> 2. Flex 布局是轴线布局，只能指定"项目"针对轴线的位置，可以看作是**一维布局**。
> 3. Grid 布局则是将容器划分成"行"和"列"，产生单元格，然后指定"项目所在"的单元格，可以看作是**二维布局**。

## 2.基本用法

~~~css
/*容器用法*/
div{
    display:grid;/*inline-grid*/
    grid-template-columns: 100px 100px 100px;/*定义每一列的列宽*/
    grid-template-rows: 100px 100px 100px;/*定义每一行的行高*/
    grid-template-columns: 33.33% 33.33% 33.33%;
  	grid-template-rows: 33.33% 33.33% 33.33%;
    grid-template-columns: repeat(3, 33.33%);/*简化重复的值*/
    grid-template-rows: repeat(3, 33.33%);
    grid-template-columns: repeat(auto-fill, 100px);/*每一行（或每一列）容纳尽可能多的单元格*/
    grid-template-columns: 1fr 1fr;/*grid-template-columns: 1fr 1fr*/
    /*gap: <row-gap> <column-gap>;*/
    row-gap: 20px;/*设置行与行的间隔（行间距）*/
    column-gap: 20px;/*设置列与列的间隔（列间距）*/
    /*定义区域*/
    grid-template-areas:'a b c'
                       	'd e f'
                       	'g h i';
    grid-auto-flow: column;/*row"先行后列";olumn"先列后行"*/
    grid-auto-flow: row dense;/*项目指定位置以后，剩下的项目怎么自动放置*/
}
/*项目用法*/
.container {
  place-items: <align-items> <justify-items>;/*单元格的位置*/
  justify-items: start | end | center | stretch;/*单元格内容的水平位置*/
  align-items: start | end | center | stretch;/*单元格内容的垂直位置*/
  place-content: <align-content> <justify-content> /*整个内容区域在容器里面的位置*/
  justify-content: start | end | center | stretch | space-around | space-between | space-evenly;
  align-content: start | end | center | stretch | space-around | space-between | space-evenly; 
}
/*浏览器自动创建的多余网格的列宽和行高*/
.container {
  display: grid;
  grid-template-columns: 100px 100px 100px;
  grid-template-rows: 100px 100px 100px;
  grid-auto-rows: 50px; 
}
/*
grid-column-start属性：左边框所在的垂直网格线
grid-column-end属性：右边框所在的垂直网格线
grid-row-start属性：上边框所在的水平网格线
grid-row-end属性：下边框所在的水平网格线
*/
.item-1 {
  grid-column: <start-line> / <end-line>;
  grid-row: <start-line> / <end-line>;
  grid-column-start: 2;
  grid-column-end: 4;
}



~~~

