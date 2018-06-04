###描述z-index以及堆叠上下文是如何形成的。  
CSS中的z-index属性控制重叠元素的垂直叠加顺序。z-index仅影响position值非static的元素。  
如果没有设置z-index值，元素将按照它们在DOM中出现的顺序堆叠（在同一层级中最低的一个出现在顶部）。非static定位的元素（及其子元素）将始终显示在默认（static）定位的元素的顶部，而与HTML层次无关。
堆叠上下文指一个元素中包含了一组子元素。在一个的堆叠上下文中，z-index的值是相对该元素设置的（并不是相对根元素）。如果元素B位于元素A的顶部，元素A的子元素C即使具有高于元素B的z-index值，子元素C的也永远不会高于元素B。
每个堆叠上下文都是自包含的 - 在堆叠元素的内容之后，整个元素将按照父堆叠上下文的堆叠顺序进行考虑。一些CSS属性会触发一个新的堆栈上下文，比如opacity小于1，filter值非none，以及transform值非none。
[原文](https://github.com/yangshun/front-end-interview-handbook/blob/master/questions/css-questions.md#describe-z-index-and-how-stacking-context-is-formed)

###描述块格式化上下文（BFC）及其工作原理。
一个块级格式化上下文（BFC）是CSS对一个页面进行可视化渲染时产生的区域，在这个区域中会产生被渲染的盒子模型。浮动、绝对定位元素，inline-blocks, table-cells, table-captions, 以及overflow属性值不为visible的元素建立新的块级上下文。
BFC是满足下列条件之一的HTML框：
float值非none；
position值不是static或者relative（为absolute或fixed）；
display值是table-cell, table-caption, inline-block, flex, 或inline-flex；
overflow值非visible；

BFC布局规则：

内部的Box会在垂直方向，一个接一个地放置。
Box垂直方向的距离由margin决定。属于同一个BFC的两个相邻Box的margin会发生重叠
每个元素的margin box的左边， 与包含块border box的左边相接触(对于从左往右的格式化，否则相反)。即使存在浮动也是如此。
BFC的区域不会与float box重叠。
BFC就是页面上的一个隔离的独立容器，容器里面的子元素不会影响到外面的元素。反之也如此。
计算BFC的高度时，浮动元素也参与计算

https://www.cnblogs.com/lhb25/p/inside-block-formatting-ontext.html