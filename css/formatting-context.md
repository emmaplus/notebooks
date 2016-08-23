# Box

Box是css布局的对象和基本单位,直观点来说,就是一个页面是由很多个Box组成的.元素的类型和display属性决定了这个Box的类型

* block-level box : display 属性为block, list-item, table的元素, 会参与 block formatting context 
* inline-level box: display 属性为inline, inline-block, inline-table 的元素, 会参与 inline formatting context 
* run-in box : css3中才有

# Formatting context

Formatting context 是页面中的一块渲染区域,并且有一套渲染规则,它决定了其子元素将如何定位,以及和其他元素的关系和相互作用.

最常见的Formatting context有 Block formatting context (简称BFC) 和 Inline formatting context (简称IFC).

CSS2.1中只有BFC 和 IFC ,CSS3中还增加了GFC 和 EFC.

# BFC 定义

直译:块级格式化上下文,它是一个独立的渲染区域,只有Block-level Box参与

## BFC 特性

* 内部的Box会在垂直方向,一个接一个地放置
* Box垂直方向的距离由margin决定.属于同一个BFC的两个相邻Box的margin会发生重叠,每个元素的margin box的左边,与包含块border box的左边相接触.即使存在浮动也是如此.
* BFC的区域不会与float box重叠
* BFC就是页面上的一个隔离的独立容器,容器里面的子元素不会影响到外面的元素.反之也如此.
* 计算BFC的高度时,浮动元素也参与计算.

## 哪些元素会生成BFC

* 根元素
* float属性不为none
* position为absolute或fixed
* display为inline-block,table-cell,table-caption,flex,inline-flex
* overflow不为visible

### _问题:_ 

* display 为inline-block的是inline-level box ,而只有block-level box 参与BFC,那为什么这里会说display为inline-block的会生成BFC呢?