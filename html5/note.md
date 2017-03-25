# html学习笔记

标签（空格分隔）： html5 web开发

---

1、基本格式
------

   

    <!DOCTYPE html> <!--html5标签-->
    <html>
    <head>
    	<title></title>
    </head>
    <body>
    
    </body>
    </html>

**[HTML 4.01 快速参考/速查手册][1]**
**[head部分][2]**

---

2、HTML5 中的一些有趣的**新特性**：
-----------------------

用于绘画的 canvas 元素
用于媒介回放的 video 和 audio 元素
对本地离线存储的更好的支持
新的特殊内容元素，比如 article、footer、header、nav、section
新的表单控件，比如 calendar、date、time、email、url、search

**布局：**
HTML5 提供的新语义元素定义了网页的不同部分：

> header	定义文档或节的页眉 
nav	定义导航链接的容器 
section	定义文档中的节 
article	定义独立的自包含文章
aside	定义内容之外的内容（比如侧栏） 
footer	定义文档或节的页脚 
details	定义额外的细节 summary	定义
> details 元素的标题

HTML5 定义了八个新的语义 HTML 元素。所有都是块级元素。
您可以把 CSS display 属性设置为 block，以确保老式浏览器中正确的行为：

    header, section, footer, aside, nav, main, article, figure {
        display: block; 
    }
[新元素及属性][3]

 [canvas][4]
HTML5 的 canvas 元素使用 JavaScript 在网页上绘制图像。
画布是一个矩形区域，您可以控制其每一像素。
canvas 拥有多种绘制路径、矩形、圆形、字符以及添加图像的方法。

创建 Canvas 元素
规定元素的 id、宽度和高度：

    <canvas id="myCanvas" width="200" height="100"></canvas>
    
canvas 元素本身是没有绘图能力的。所有的绘制工作必须在 JavaScript 内部完成：
getContext("2d") 对象是内建的 HTML5 对象，拥有多种绘制路径、矩形、圆形、字符以及添加图像的方法。

    <script type="text/javascript">
    var c=document.getElementById("myCanvas"); //使用 id 来寻找 canvas 元素
    var cxt=c.getContext("2d"); //创建 context 对象
    cxt.fillStyle="#FF0000"; //绘制一个红色的矩形
    cxt.fillRect(0,0,150,75);
    </script>
fillStyle 方法将其染成红色，fillRect 方法规定了形状、位置和尺寸。
fillRect 方法拥有参数 (0,0,150,75)。意思是：在画布上绘制 150x75 的矩形，从左上角开始 (0,0)。

[SVG][5]
什么是SVG？

 - SVG 指可伸缩矢量图形 (Scalable Vector Graphics)
 - SVG 用于定义用于网络的基于矢量的图形
 - SVG 使用 XML 格式定义图形
 - SVG 图像在放大或改变尺寸的情况下其图形质量不会有损失
 - SVG 是万维网联盟的标准

与其他图像格式相比（比如 JPEG 和 GIF），使用 SVG 的优势在于：

 - SVG 图像可通过文本编辑器来创建和修改
 - SVG 图像可被搜索、索引、脚本化或压缩
 - SVG 是可伸缩的
 - SVG 图像可在任何的分辨率下被高质量地打印
 - SVG 可在图像质量不下降的情况下被放大

在 HTML5 中，您能够将 SVG 元素直接嵌入 HTML 页面中：

    <!DOCTYPE html>
    <html>
    <body>
    
    <svg xmlns="http://www.w3.org/2000/svg" version="1.1" height="190">
      <polygon points="100,10 40,180 190,60 10,60 160,180"
      style="fill:lime;stroke:purple;stroke-width:5;fill-rule:evenodd;" />
    </svg>
    
    </body>
    </html>

多媒体 video audio embed
video 元素支持三种视频格式
Ogg = 带有 Theora 视频编码和 Vorbis 音频编码的 Ogg 文件
MPEG4 = 带有 H.264 视频编码和 AAC 音频编码的 MPEG 4 文件
WebM = 带有 VP8 视频编码和 Vorbis 音频编码的 WebM 文件

在 HTML5 中显示视频，您所有需要的是：

    <video src="movie.ogg" controls="controls">
    </video>
control 属性供添加播放、暂停和音量控件。
包含宽度和高度属性也是不错的主意。
标签中间插入的是供不支持 video 元素的浏览器显示的提示信息。
video 元素允许多个 source 元素。source 元素可以链接不同的视频文件。浏览器将使用第一个可识别的格式
属性	值	描述
autoplay	autoplay	如果出现该属性，则视频在就绪后马上播放。
controls	controls	如果出现该属性，则向用户显示控件，比如播放按钮。
height	pixels	设置视频播放器的高度。
loop	loop	如果出现该属性，则当媒介文件完成播放后再次开始播放。
preload	preload	
如果出现该属性，则视频在页面加载时进行加载，并预备播放。
如果使用 "autoplay"，则忽略该属性。
src	url	要播放的视频的 URL。
width	pixels	设置视频播放器的宽度。

audio 元素支持三种音频格式：Ogg Vorbis、 MP3、 Wav
在 HTML5 中播放音频，您所有需要的是：

    <audio src="song.ogg" controls="controls">
    </audio>

control 属性供添加播放、暂停和音量控件。
标签之间插入的内容是供不支持 audio 元素的浏览器显示的：
属性	值	描述
autoplay	autoplay	如果出现该属性，则音频在就绪后马上播放。
controls	controls	如果出现该属性，则向用户显示控件，比如播放按钮。
loop	loop	如果出现该属性，则每当音频结束时重新开始播放。
preload	preload	
如果出现该属性，则音频在页面加载时进行加载，并预备播放。
如果使用 "autoplay"，则忽略该属性。
src	url	要播放的音频的 URL。

[拖放][6]

    <!DOCTYPE HTML>
    <html>
    <head>
    <script type="text/javascript">
    function allowDrop(ev)
    {
    ev.preventDefault();
    }
    
    function drag(ev)
    {
    ev.dataTransfer.setData("Text",ev.target.id);//设置被拖数据的数据类型和值
    }
    
    function drop(ev)
    {
    ev.preventDefault();
    var data=ev.dataTransfer.getData("Text");
    ev.target.appendChild(document.getElementById(data));
    }
    </script>
    </head>
    <body>
    
    <!--
    ondragover 事件规定在何处放置被拖动的数据-
    当放置被拖数据时，会发生 drop 事件
    ->
    <div id="div1" ondrop="drop(event)"
    ondragover="allowDrop(event)"></div>
    <img id="drag1" src="img_logo.gif" draggable="true"
    ondragstart="drag(event)" width="336" height="69" />
    <!--为了使元素可拖动，把 draggable 属性设置为 true-->
    
    </body>
    </html>
代码解释：

 - 调用 preventDefault() 来避免浏览器对数据的默认处理（drop 事件的默认行为是以链接形式打开）
 - 通过 dataTransfer.getData("Text") 方法获得被拖的数据。该方法将返回在 setData() 方法中设置为相同类型的任何数据。
 - 被拖数据是被拖元素的 id ("drag1")
 - 把被拖元素追加到放置元素（目标元素）中


 ---

3、原有的html常用标签
-------------

标题（Heading）是通过 `<h1> - <h6>` 等标签进行定义的。
实例

    <h1>This is a heading</h1>
    <h2>This is a heading</h2>
    <h3>This is a heading</h3>

段落是通过 `<p>` 标签进行定义的。
实例

    <p>This is a paragraph.</p>
    <p>This is another paragraph.</p>

链接是通过 `<a>` 标签进行定义的。
实例

    <a href="http://www.w3school.com.cn">This is a link</a>

图像是通过 `<img>` 标签进行定义的。
实例

    <img src="w3school.jpg" width="104" height="142" />
    
`<br />` 标签定义换行
`&nbsp;`空格占位符

适用于大多数 HTML 元素的属性：[属性参考表][7]

    属性	值	描述
    class	classname	规定元素的类名（classname）
    id	id	规定元素的唯一 id
    style	style_definition	规定元素的行内样式（inline style）
    title	text	规定元素的额外信息（可在工具提示中显示）

注释
可以将注释插入 HTML 代码中，这样可以提高其可读性，使代码更易被人理解。浏览器会忽略注释，也不会显示它们。
注释是这样写的：

    <!-- This is a comment -->
水平线
`<hr />` 标签在 HTML 页面中创建水平线。
hr 元素可用于分隔内容。

style样式
background-color 属性为元素定义了背景颜色
font-family、color 以及 font-size 属性分别定义元素中文本的字体系列、颜色和字体尺寸
text-align 属性规定了元素中文本的水平对齐方式

**[文本格式化常见情况][8]**
HTML `<q>` 元素定义短的引用。
浏览器通常会为 `<q>` 元素包围引号。

HTML `<blockquote>` 元素定义被引用的节。
浏览器通常会对 `<blockquote>` 元素进行缩进处理。

其他常见标签具体
[img标签][9]
[a标签][10]
[table标签][11]
[ul ol标签][12]

**HTML表单**
用于收集用户输入
 `<form>`元素定义html表单
 [常见元素及属性：][13]
包含不同类型的 input 元素、复选框、单选按钮、提交按钮等等。

 `<input>`元素是最重要的表单元素,有很多形态，根据不同的 type 属性。
 类型	描述
text	定义常规文本输入。
radio	定义单选按钮输入（选择多个选择之一）
submit	定义提交按钮（提交表单）

文本输入
`<input type="text">` 定义用于文本输入的单行输入字段：

    <form>
     First name:<br>
    <input type="text" name="firstname">
    <br>
     Last name:<br>
    <input type="text" name="lastname">
    </form> 
    
单选按钮输入
`<input type="radio">` 定义单选按钮。
单选按钮允许用户在有限数量的选项中选择其中之一：

    <form>
    <input type="radio" name="sex" value="male" checked>Male
    <br>
    <input type="radio" name="sex" value="female">Female
    </form> 

提交按钮
`<input type="submit">` 定义用于向表单处理程序（form-handler）提交表单的按钮。
表单处理程序通常是包含用来处理输入数据的脚本的服务器页面。
表单处理程序在表单的 action 属性中指定：

    <form action="action_page.php">
    First name:<br>
    <input type="text" name="firstname" value="Mickey">
    <br>
    Last name:<br>
    <input type="text" name="lastname" value="Mouse">
    <br><br>
    <input type="submit" value="Submit">
    </form> 

action 属性定义在提交表单时执行的动作。
向服务器提交表单的通常做法是使用提交按钮。
通常，表单会被提交到 web 服务器上的网页。
在上面的例子中，指定了某个服务器脚本来处理被提交表单：    `<form action="action_page.php">`
如果省略 action 属性，则 action 会被设置为当前页面。

method 属性规定在提交表单时所用的 HTTP 方法（GET 或 POST）：
`<form action="action_page.php" method="GET">`
如果表单提交是被动的（比如搜索引擎查询），并且没有敏感信息。最适合少量数据的提交。浏览器会设定容量限制。
`<form action="action_page.php" method="POST">`
如果表单正在更新数据，或者包含敏感信息（例如密码）。
POST 的安全性更加，因为在页面地址栏中被提交的数据是不可见的。

Name 属性
如果要正确地被提交，每个输入字段必须设置一个 name 属性。
本例只会提交 "Last name" 输入字段：

    <form action="action_page.php">
    First name:<br>
    <input type="text" value="Mickey">
    <br>
    Last name:<br>
    <input type="text" name="lastname" value="Mouse">
    <br><br>
    <input type="submit" value="Submit">
    </form>
    
`<fieldset>` 元素组合表单中的相关数据
`<legend>` 元素为 `<fieldset>` 元素定义标题。

    <form action="action_page.php">
    <fieldset>
    <legend>Personal information:</legend>
    First name:<br>
    <input type="text" name="firstname" value="Mickey">
    <br>
    Last name:<br>
    <input type="text" name="lastname" value="Mouse">
    <br><br>
    <input type="submit" value="Submit"></fieldset>
    </form> 
    
`<select>` 元素定义下拉列表：

    <select name="cars">
    <option value="volvo">Volvo</option>
    <option value="saab">Saab</option>
    <option value="fiat">Fiat</option>
    <option value="audi">Audi</option>
    </select>
    
`<option>` 元素定义待选择的选项。
列表通常会把首个选项显示为被选选项。
您能够通过添加 selected 属性来定义预定义选项。
实例`<option value="fiat" selected>Fiat</option>`

`<textarea>` 元素定义多行输入字段（文本域）：

    <textarea name="message" rows="10" cols="30">
    The cat was playing in the garden.
    </textarea>
    
`<button>` 元素定义可点击的按钮：

    <button type="button" onclick="alert('Hello World!')">Click Me!</button>
    
HTML5 增加了如下表单元素：`<datalist> <keygen> <output>`

`<datalist>` 元素为 `<input>` 元素规定预定义选项列表。
用户会在他们输入数据时看到预定义选项的下拉列表。
`<input>` 元素的 list 属性必须引用 `<datalist>` 元素的 id 属性。

    <form action="action_page.php">
    <input list="browsers">
    <datalist id="browsers">
       <option value="Internet Explorer">
       <option value="Firefox">
       <option value="Chrome">
       <option value="Opera">
       <option value="Safari">
    </datalist> 
    </form>

`<input type="password">` 定义密码字段：

    <form>
     User name:<br>
    <input type="text" name="username">
    <br>
     User password:<br>
    <input type="password" name="psw">
    </form>  
password 字段中的字符会被做掩码处理（显示为星号或实心圆）。

`<input type="checkbox">` 定义复选框。
Checkboxes let a user select ZERO or MORE options of a limited number of choices.

    <form>
    <input type="checkbox" name="vehicle" value="Bike">I have a bike
    <br>
    <input type="checkbox" name="vehicle" value="Car">I have a car 
    </form> 
    
HTML5 增加了多个新的输入类型：color、date、datetime、datetime-local、email、month、number、range、search、tel、time、url、week

[input属性][14]






 
---
4、CSS样式
-------
外部样式表

    <head>
    <link rel="stylesheet" type="text/css" href="mystyle.css">
    </head>

内部样式表
你可以在 head 部分通过 `<style>` 标签定义内部样式表。

    <head>
    
    <style type="text/css">
    body {background-color: red}
    p {margin-left: 20px}
    </style>
    </head>
内联样式 在相关的标签中使用样式属性

    <p style="color: red; margin-left: 20px">
    This is a paragraph
    </p>

---
5、块
---
HTML 块元素
大多数 HTML 元素被定义为块级元素或内联元素。
“块级元素”译为 block level element，“内联元素”译为 inline element。
块级元素在浏览器显示时，通常会以新行来开始（和结束）。
例子：`<h1>, <p>, <ul>, <table>`

HTML 内联元素
内联元素在显示时通常不会以新行开始。
例子：`<b>, <td>, <a>, <img>`

 `<div>` 元素是块级元素，它是可用于组合其他 HTML 元素的容器，没有特定的含义。
与 CSS 一同使用，用于对大的内容块设置样式属性。另一个常见的用途是文档布局 。

`<span>` 元素是内联元素，可用作文本的容器，也没有特定的含义。
当与 CSS 一同使用时，可用于为部分文本设置样式属性。

***类***
对 HTML 进行分类（设置类），使我们能够为元素的类定义 CSS 样式。
为相同的类设置相同的样式，或者为不同的类设置不同的样式。
此时div/span用作其他 HTML 元素的容器。为相同的div/span设置相同的类。
用.来选择类

---

6、响应式设计
-------
什么是响应式 Web 设计？

 - RWD 指的是响应式 Web 设计（Responsive Web Design） 
 - RWD 能够以可变尺寸传递网页 RWD
 - 对于平板和移动设备是必需的
 - 一般使用 **Bootstrap**

 

---
7、框架
------
通过使用框架，你可以在同一个浏览器窗口中显示不止一个页面。每份HTML文档称为一个框架，并且每个框架都独立于其他的框架。
使用框架的坏处：

 - 开发人员必须同时跟踪更多的HTML文档
 - 很难打印整张页面

框架结构标签`<frameset>`定义如何将窗口分割为框架
每个 frameset 定义了一系列行或列
rows/columns 的值规定了每行或每列占据屏幕的面积

框架标签（Frame）
Frame 标签定义了放置在每个框架中的 HTML 文档。
在下面的这个例子中，我们设置了一个两列的框架集。第一列被设置为占据浏览器窗口的 25%。第二列被设置为占据浏览器窗口的 75%。HTML 文档 "frame_a.htm" 被置于第一个列中，而 HTML 文档 "frame_b.htm" 被置于第二个列中：

    <frameset cols="25%,75%">
       <frame src="frame_a.htm">
       <frame src="frame_b.htm">
    </frameset>
    
假如一个框架有可见边框，用户可以拖动边框来改变它的大小。为了避免这种情况发生，可以在 `<frame>` 标签中加入：noresize="noresize"。
[更多实例][15]

内联框架
    `<iframe src="URL"></iframe>`
1、height 和 width 属性用于规定 iframe 的高度和宽度。
属性值的默认单位是像素，但也可以用百分比来设定（比如 "80%"）。

2、frameborder 属性规定是否显示 iframe 周围的边框。
设置属性值为 "0" 就可以移除边框。

3、iframe 可用作链接的目标（target）。
链接的 target 属性必须引用 iframe 的 name 属性



[实体符号参考表][16]
[颜色表][17]


  [1]: http://www.w3school.com.cn/html/html_quick.asp
  [2]: http://www.w3school.com.cn/html/html_head.asp
  [3]: http://www.w3school.com.cn/html/html5_new_elements.asp
  [4]: http://www.w3school.com.cn/html/html5_canvas.asp
  [5]: http://www.w3school.com.cn/html/html5_svg.asp
  [6]: http://www.w3school.com.cn/html5/html_5_draganddrop.asp
  [7]: http://www.w3school.com.cn/tags/html_ref_standardattributes.asp
  [8]: http://www.w3school.com.cn/html/html_formatting.asp
  [9]: http://www.w3school.com.cn/html/html_images.asp
  [10]:http://www.w3school.com.cn/html/html_links.asp
  [11]:http://www.w3school.com.cn/html/html_tables.asp
  [12]:http://www.w3school.com.cn/html/html_lists.asp
  [13]: http://www.w3school.com.cn/html/html_forms.asp
  [14]: http://www.w3school.com.cn/html/html_form_attributes.asp
  [15]: http://www.w3school.com.cn/html/html_frames.asp
  [16]: http://www.w3school.com.cn/tags/html_ref_entities.html
  [17]: http://www.w3school.com.cn/html/html_colornames.asp