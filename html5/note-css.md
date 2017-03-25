# CSS3学习笔记

标签（空格分隔）： css css3 web 前端

---

CSS 概述

 - CSS 指层叠样式表 (Cascading Style Sheets)
 - 样式定义如何显示 HTML 元素
 - 样式通常存储在样式表中
 - 把样式添加到 HTML 4.0 中，是为了解决内容与表现分离的问题
 - 外部样式表可以极大提高工作效率
 - 外部样式表通常存储在 CSS 文件中
 - 多个样式定义可层叠为一

CSS 规则由两个主要的部分构成：选择器，以及一条或多条声明。

    selector {declaration1; declaration2; ... declarationN }

选择器通常是您需要改变样式的 HTML 元素。
每条声明由一个属性和一个值组成。
属性（property）是您希望设置的样式属性（style attribute）。每个属性有一个值。属性和值被冒号分开。`selector {property: value}`
![css规则][1]
多重属性时可以在每行只描述一个属性，这样可以增强样式定义的可读性。

    body {
      color: #000;
      background: #fff;
      margin: 0;
      padding: 0;
      font-family: Georgia, Palatino, serif;
      }

**几种选择器**
id选择器
类选择器
属性选择器

**插入CSS的三种方案**
外部样式表
当样式需要应用于很多页面时，外部样式表将是理想的选择。在使用外部样式表的情况下，你可以通过改变一个文件来改变整个站点的外观。每个页面使用 <link> 标签链接到样式表。<link> 标签在（文档的）头部：

    <head>
    <link rel="stylesheet" type="text/css" href="mystyle.css" />
    </head>
    
内部样式表
当单个文档需要特殊的样式时，就应该使用内部样式表。你可以使用 <style> 标签在文档头部定义内部样式表，就像这样:

    <head>
    <style type="text/css">
      hr {color: sienna;}
      p {margin-left: 20px;}
      body {background-image: url("images/back40.gif");}
    </style>
    </head>

内联样式
由于要将表现和内容混杂在一起，内联样式会损失掉样式表的许多优势。请慎用这种方法，例如当样式仅需要在一个元素上应用一次时。
要使用内联样式，你需要在相关的标签内使用样式（style）属性。Style 属性可以包含任何 CSS 属性。本例展示如何改变段落的颜色和左外边距：

    <p style="color: sienna; margin-left: 20px">
    This is a paragraph
    </p>

 [背景样式][2]
相对于可视区是固定的（**fixed**）
[文本样式][3]
[字体样式][4]

链接的四种状态：

 - a:link - 普通的、未被访问的链接 
 - a:visited - 用户已访问的链接 
 - a:hover - 鼠标指针位于链接的上方
 - a:active - 链接被点击的时刻

---
**盒子模型**
![盒子模型示意图][5]
元素框的最内部分是实际的内容，直接包围内容的是内边距。内边距呈现了元素的背景。内边距的边缘是边框。边框以外是外边距，外边距默认是透明的，因此不会遮挡其后的任何元素。
内边距、边框和外边距都是可选的，默认值是零。通过设置来覆盖浏览器样式：

    * {
      margin: 0;
      padding: 0;
    }
width 和 height 指的是内容区域的宽度和高度。增加内边距、边框和外边距不会影响内容区域的尺寸，但是会增加元素框的总尺寸。

![长宽][6]

提示：内边距、边框和外边距可以应用于一个元素的所有边，也可以应用于单独的边。
提示：外边距可以是负值，而且在很多情况下都要使用负值的外边距。
border-style 的默认值是 none 。
采用了 top-right-bottom-left 的顺序。
外边距合并指的是，当两个垂直外边距相遇时，它们将形成一个外边距。合并后的外边距的高度等于两个发生合并的外边距的高度中的较大者。
![此处输入图片的描述][7]
当一个元素包含在另一个元素中时（假设没有内边距或边框把外边距分隔开），它们的上和/或下外边距也会发生合并。
![此处输入图片的描述][8]
假设有一个空元素，它有外边距，但是没有边框或填充。在这种情况下，上外边距与下外边距就碰到了一起，它们会发生合并
![此处输入图片的描述][9]
如果这个外边距遇到另一个元素的外边距，它还会发生合并：
![此处输入图片的描述][10]

---
**定位**
定位的基本思想很简单，它允许你定义元素框相对于其正常位置应该出现的位置，或者相对于父元素、另一个元素甚至浏览器窗口本身的位置。

div、h1 或 p 元素常常被称为块级元素。这意味着这些元素显示为一块内容，即“块框”。与之相反，span 和 strong 等元素称为“行内元素”，这是因为它们的内容显示在行中，即“行内框”。

可以使用 display 属性改变生成的框的类型。这意味着，通过将 display 属性设置为 block，可以让行内元素（比如 <a> 元素）表现得像块级元素一样。还可以通过把 display 设置为 none，让生成的元素根本没有框。这样的话，该框及其所有内容就不再显示，不占用文档中的空间。

CSS 有三种基本的定位机制：普通流、浮动和绝对定位。
除非专门指定，否则所有框都在普通流中定位。

块级框从上到下一个接一个地排列，框之间的垂直距离是由框的垂直外边距计算出来。
行内框在一行中水平布置。可以使用水平内边距、边框和外边距调整它们的间距。但是，垂直内边距、边框和外边距不影响行内框的高度。由一行形成的水平框称为行框（Line Box），行框的高度总是足以容纳它包含的所有行内框。不过，设置行高可以增加这个框的高度。

position 属性值的含义：
**static**
元素框正常生成。块级元素生成一个矩形框，作为文档流的一部分，行内元素则会创建一个或多个行框，置于其父元素中。
**relative**
元素框偏移某个距离。元素仍保持其未定位前的形状，它原本所占的空间仍保留。
**absolute**
元素框从文档流完全删除，并相对于其包含块定位。包含块可能是文档中的另一个元素或者是初始包含块。元素原先在正常文档流中所占的空间会关闭，就好像元素原来不存在一样。元素定位后生成一个块级框，而不论原来它在正常流中生成何种类型的框。
**fixed**
元素框的表现类似于将 position 设置为 absolute，不过其包含块是视窗本身。
提示：相对定位实际上被看作普通流定位模型的一部分，因为元素的位置相对于它在普通流中的位置。

相对定位
![此处输入图片的描述][11]
注意，在使用相对定位时，无论是否进行移动，元素仍然占据原来的空间。因此，移动元素会导致它覆盖其它框。

绝对定位
绝对定位使元素的位置与文档流无关，因此不占据空间。这一点与相对定位不同，相对定位实际上被看作普通流定位模型的一部分，因为元素的位置相对于它在普通流中的位置。
![此处输入图片的描述][12]
绝对定位的元素的位置相对于最近的已定位祖先元素，如果元素没有已定位的祖先元素，那么它的位置相对于最初的包含块。

浮动 float
下图，当把框 1 向右浮动时，它脱离文档流并且向右移动，直到它的右边缘碰到包含框的右边缘：
![右浮动][13]
下图，当框 1 向左浮动时，它脱离文档流并且向左移动，直到它的左边缘碰到包含框的左边缘。因为它不再处于文档流中，所以它不占据空间，实际上覆盖住了框 2，使框 2 从视图中消失。
如果把所有三个框都向左移动，那么框 1 向左浮动直到碰到包含框，另外两个框向左浮动直到碰到前一个浮动框。
![左浮动][14]
下图，如果包含框太窄，无法容纳水平排列的三个浮动元素，那么其它浮动块向下移动，直到有足够的空间。如果浮动元素的高度不同，那么当它们向下移动时可能被其它浮动元素“卡住”：
![特殊][15]
浮动框旁边的行框被缩短，从而给浮动框留出空间，行框围绕浮动框。
因此，创建浮动框可以使文本围绕图像
![此处输入图片的描述][16]
要想阻止行框围绕浮动框，需要对该框应用 clear 属性。clear 属性的值可以是 left、right、both 或 none，它表示框的哪些边不应该挨着浮动框。
为了实现这种效果，在被清理的元素的上外边距上添加足够的空间，使元素的顶边缘垂直下降到浮动框下面：
![此处输入图片的描述][17]

实例
[水平菜单][18]

伪类

伪元素
:first-line 伪元素用于向文本的首行设置特殊样式。
在下面的例子中，浏览器会根据 "first-line" 伪元素中的样式对 p 元素的第一行文本进行格式化：
实例

    p:first-line
      {
      color:#ff0000;
      font-variant:small-caps;
      }
注释："first-line" 伪元素只能用于块级元素。
注释：下面的属性可应用于 "first-line" 伪元素：
font
color
background
word-spacing
letter-spacing
text-decoration
vertical-align
text-transform
line-height
clear

:first-letter 伪元素用于向文本的首字母设置特殊样式：

    p:first-letter
      {
      color:#ff0000;
      font-size:xx-large;
      }
注同上

 :before 伪元素可以在元素的内容前面插入新内容。
下面的例子在每个 <h1> 元素前面插入一幅图片：

    h1:before
      {
      content:url(logo.gif);
      }
:after 伪元素可以在元素的内容之后插入新内容。

[对齐][19]
margin水平对齐
position/float左右对齐

---
**CSS3**
CSS3 被划分为模块。
其中最重要的 CSS3 模块包括：
选择器
框模型
背景和边框
文本效果
2D/3D 转换
动画
多列布局
用户界面

通过 CSS3，您能够创建圆角边框，向矩形添加阴影，使用图片来绘制边框 - 并且不需使用设计软件，比如 PhotoShop。
在本章中，您将学到以下边框属性：
border-radius 创建圆角矩形
box-shadow 向方框添加阴影
border-image 用图片创建边框

CSS3 包含多个新的背景属性，它们提供了对背景更强大的控制。
在本章，您将学到以下背景属性：
background-size
background-origin 规定背景图片的定位区域

CSS3 包含多个新的文本特性
text-shadow 文本阴影
word-wrap 自动换行

字体是在 CSS3 @font-face 规则中定义的

转换
通过 CSS3 转换，我们能够对元素进行移动、缩放、转动、拉长或拉伸。
转换是使元素改变形状、尺寸和位置的一种效果。

[2D 转换方法][20]
translate()
rotate()
scale()
skew()
matrix()

[3D 转换方法][21]
rotateX()
rotateY()

[过渡][22]
通过 CSS3，我们可以在不使用 Flash 动画或 JavaScript 的情况下，当元素从一种样式变换为另一种样式时为元素添加效果。

CSS3 过渡是元素从一种样式逐渐改变为另一种的效果。
要实现这一点，必须规定两项内容：
规定您希望把效果添加到哪个 CSS 属性上
规定效果的时长

[动画][23]
通过 CSS3，我们能够创建动画，这可以在许多网页中取代动画图片、Flash 动画以及 JavaScript。

[多列][24]
通过 CSS3，您能够创建多个列来对文本进行布局 - 就像报纸那样！
如下多列属性：
column-count
column-gap
column-rule

[用户界面][25]
在 CSS3 中，新的用户界面特性包括重设元素尺寸、盒尺寸以及轮廓等。
在本章中，您将学到以下用户界面属性：
resize
box-sizing
outline-offset


---


  
  


  [1]: http://www.w3school.com.cn/i/ct_css_selector.gif
  [2]: http://www.w3school.com.cn/css/css_background.asp
  [3]: http://www.w3school.com.cn/css/css_text.asp
  [4]: http://www.w3school.com.cn/css/css_font.asp
  [5]: http://www.w3school.com.cn/i/ct_boxmodel.gif
  [6]: http://www.w3school.com.cn/i/ct_css_boxmodel_example.gif
  [7]: http://www.w3school.com.cn/i/ct_css_margin_collapsing_example_1.gif
  [8]: http://www.w3school.com.cn/i/ct_css_margin_collapsing_example_2.gif
  [9]: http://www.w3school.com.cn/i/ct_css_margin_collapsing_example_3.gif
  [10]: http://www.w3school.com.cn/i/ct_css_margin_collapsing_example_4.gif
  [11]: http://www.w3school.com.cn/i/ct_css_positioning_relative_example.gif
  [12]: http://www.w3school.com.cn/i/ct_css_positioning_absolute_example.gif
  [13]: http://www.w3school.com.cn/i/ct_css_positioning_floating_right_example.gif
  [14]: http://www.w3school.com.cn/i/ct_css_positioning_floating_left_example.gif
  [15]: http://www.w3school.com.cn/i/ct_css_positioning_floating_left_example_2.gif
  [16]: http://www.w3school.com.cn/i/ct_css_positioning_floating_linebox.gif
  [17]: http://www.w3school.com.cn/i/ct_css_positioning_floating_clear.gif
  [18]: http://www.w3school.com.cn/tiy/t.asp?f=csse_float5
  [19]: http://www.w3school.com.cn/css/css_align.asp
  [20]: http://www.w3school.com.cn/css3/css3_2dtransform.asp
  [21]: http://www.w3school.com.cn/css3/css3_3dtransform.asp
  [22]: http://www.w3school.com.cn/css3/css3_transition.asp
  [23]: http://www.w3school.com.cn/css3/css3_animation.asp
  [24]: http://www.w3school.com.cn/css3/css3_multiple_columns.asp
  [25]: http://www.w3school.com.cn/css3/css3_user_interface.asp