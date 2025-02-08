# CSS

## CSS语法

CSS规则由两个主要的部分构成：**选择器**，以及一条或多条**声明**：

* **选择器**通常是需要改变样式的HTML元素。
* 每条**声明**由一个属性和一个值组成。
  * **属性**（property）是希望设置的样式属性（style attribute）。每个属性有一个值。属性和值被冒号分开。
* **CSS声明**总是以分号`;`结束，声明总以大括号`{}`括起来。
* **CSS注释**以`/*`开始，以`*/`结束。

![CSS语法](CSS%E5%AD%A6%E4%B9%A0_img/1_CSS%E8%AF%AD%E6%B3%95.jpg)

## CSS选择器

### id选择器

* id选择器可以为标有特定id的HTML元素指定特定的样式。
* HTML元素以id属性来设置id选择器，CSS中id选择器以`#`来定义。
* id属性不能以数字开头，数字开头的id在 Mozilla/Firefox 浏览器中不起作用。
  
```css
/*应用于元素属性id="para1"的样式规则*/ 
#para1 {
    text-align:center;
    color:red;
}
```

### class选择器

* class选择器用于描述一组元素的样式，class选择器有别于id选择器，class可以在多个元素中使用。
* class选择器在HTML中以class属性表示，在CSS中，类选择器以一个点`.`号显示。
  
```css
/*所有拥有center类的HTML元素居中*/
.center { text-align:center; }
/*指定特定的HTML元素(所有p元素)使用class*/
p.center { text-align:center; }
```

### 通用选择器（*）

```html
<style>
    /*将所有 HTML 元素的内边距和外边距都设置为0。*/
    * {
        margin: 0;
        padding: 0;
    }
</style>
```

### 元素(类型)选择器

```html
<style>
    /*将所有段落的文本颜色都设置为蓝色。*/
    p {
        color: blue;
    }
</style>
```

### 属性选择器

```html
<style>
    /*将所有带有 href 属性的元素的下划线去掉。*/
    [href] {
        text-decoration: none;
    }
    input[type='text']{
        border: 1px solid red;
    }
    .v1[type='text']{
    color: gold;
}
</style>

<a href="#">这是一个链接</a>
<input type="text">
<div class="v1" type="text"></div>
```

### 伪类（Pseudo-classes）

`https://www.runoob.com/css/css-pseudo-classes.html`

CSS伪类是用来添加一些选择器的特殊效果。

#### 语法

伪类的语法：`selector:pseudo-class {property:value;}`
CSS类也可以使用伪类：`selector.class:pseudo-class {property:value;}`

#### anchor伪类

在支持 CSS 的浏览器中，链接的不同状态都可以以不同的方式显示

```css
a:link {color:#FF0000;} /* 未访问的链接 */
a:visited {color:#00FF00;} /* 已访问的链接 */
a:hover {color:#FF00FF;} /* 鼠标划过链接 */
a:active {color:#0000FF;} /* 已选中的链接 */
```

* `:hover` 选择器可用于所有元素，不仅是链接。
* `:link` 选择器设置了未访问过的页面链接样式，`:visited` 选择器设置访问过的页面链接的样式， `:active`选择器设置当你点击链接时的样式。
* 为了产生预期的效果，在 CSS 定义中，`:hover` 必须位于 `:link` 和 `:visited` 之后。`:active`必须被置于`:hover`之后，才是有效的。
* 伪类的名称不区分大小写。

### 后代选择器

```html
<style>
    /*在v1类中为所有层级中li标签添加样式*/
    .v1 li{
        color: pink;
    }
    /*在v1的下一层里为a标签添加样式*/
    .v1 > a{
        color: dodgerblue;
    }
</style>
<div class="v1">
    <a>百度</a>
    <div>
        <a>谷歌</a>
    </div>
    <ul>
        <li>美国</li>
        <li>日本</li>
        <li>韩国</li>
    </ul>
</div>
```

## CSS创建

### 外部样式表（External style sheet）

外部样式表适用于当样式需要应用于很多页面时。使用外部样式表时，可以通过改变一个文件来改变整个站点的外观。每个页面在HTML文档头部使用`<link>`标签链接到样式表。

```html
<head>
    <link rel="stylesheet" href="style.css">
</head>
```

浏览器会从文件`style.css`中读到样式声明，并根据它来格式化文档。
外部样式表可以在任何文本编辑器中进行编辑。文件不能包含任何的HTML标签。样式表应该以`.css`扩展名进行保存。

```css
hr {color:sienna;}
p {margin-left:20px;}
body {background-image:url("/images/back40.gif");}
/*属性值与单位之间不能留有空格（如："margin-left: 20px"），正确的写法margin-left:20px*/
```

### 内部样式表（Internal style sheet）

内部样式表适用于当单个文档需要特殊的样式时。可以在HTML头部使用`<style>`标签在文档头部定义内部样式表。

```html
<head>
    <style>
        hr {color:sinna;}
        p {margin-left:20px;}
        body {background-image:url("images/back40.gif");}
    </style>
</head>
```

### 内联样式（Inline style）

内联样式即在标签内使用样式（style）属性。`Style`属性可以包含任何CSS属性。

```html
<p style="color:sienna;margin-left:20px">这是一个段落。</p>
```

### 多重样式

如果某些属性在不同的样式表中被同样的选择器定义，那么属性值将从更具体的样式表中被继承过来。

例如，外部样式表拥有针对h3选择器的三个属性：

```css
h3
{
    color:red;
    text-align:left;
    font-size:8pt;
}
```

内部样式表拥有针对h3选择器的两个属性：

```css
h3
{
    text-align:right;
    font-size:20pt;
}
```

则h3同时链接这两个样式表后得到的样式为：

```css
color:red;
text-align:right;
font-size:20pt;
```

即颜色属性将被继承于外部样式表，而文字排列（text-alignment）和字体尺寸（font-size）会被内部样式表中的规则取代。

### 多重样式优先级

样式表允许以多种方式规定样式信息。样式可以规定在单个的HTML元素中、HTML页面头部，或在一个外部的css文件中。甚至可以在同一个HTML文档内部引用多个外部样式表。
一般情况下，优先级如下：

* **内联样式 > 内部样式 > 外部样式 > 浏览器默认样式**
* **但如果外部样式放在内部样式后面，则外部样式将覆盖内部样式**（浏览器加载HTML页面时会逐行读取，排在后面的样式会覆盖前面的样式。）
  
```html
<head>
    <!-- 设置：h3{color:blue;} -->
    <style type="text/css">
        /* 内部样式 */
        h3{color:green;}
    </style>
    <!-- 外部样式 style.css -->
    <link rel="stylesheet" type="text/css" href="style.css"/>
</head>
<body>
    <h3>显示蓝色，是外部样式</h3>
</body>
```

**优先级**是浏览器是通过判断哪些属性值与元素最相关以决定并应用到该元素上的。**优先级仅由选择器组成的匹配规则所决定。**

### 优先级顺序

下列是一份优先级逐级增加的选择器列表：

* 通用选择器（*）
* 元素(类型)选择器
* 类选择器
* 属性选择器
* 伪类
* ID 选择器
* 内联样式

![CSS优先级](CSS%E5%AD%A6%E4%B9%A0_img/2_css_weight.png)

## 背景（background）

`https://www.runoob.com/css/css-background.html`
CSS 背景属性用于定义HTML元素的背景。

### 背景颜色

background-color 属性定义了元素的背景颜色。
`body {background-color:#b0c4de;}`
CSS中，颜色值通常以以下方式定义:

* 十六进制 - 如："#ff0000"
* RGB - 如："rgb(255,0,0)"
* 颜色名称 - 如："red"

## 文本（text）

`https://www.runoob.com/css/css-text.html`

### 文本颜色

颜色属性被用来设置文字的颜色。
颜色是通过CSS最经常的指定：
    - 十六进制值 - 如: ＃FF0000
    - 一个RGB值 - 如: RGB(255,0,0)
    - 颜色的名称 - 如: red
参阅 `https://www.runoob.com/cssref/css-colors-legal.html` 查看完整的颜色值。
对于W3C标准的CSS：如果你定义了颜色属性，你还必须定义背景色属性。

```css
body {color:red;}
h1 {color:#00ff00;}
h2 {color:rgb(255,0,0);}
```

### 文本的对齐方式

文本排列属性是用来设置文本的水平对齐方式。
文本可居中或对齐到左或右,两端对齐.
当text-align设置为"justify"，每一行被展开为宽度相等，左，右外边距是对齐（如杂志和报纸）。

```css
h1 {text-align:center;}
p.date {text-align:right;}
p.main {text-align:justify;}
```

### 文本修饰

text-decoration 属性用来设置或删除文本的装饰。
`a {text-decoration:none;}`

### 文本缩进

文本缩进属性是用来指定文本的第一行的缩进。
`p {text-indent:50px;}`

## 字体

`https://www.runoob.com/css/css-font.html`
CSS字体属性定义字体，加粗，大小，文字样式。

### 字体系列

`font-family` 属性设置文本的字体系列。
`font-family` 属性应该设置几个字体名称作为一种"后备"机制，如果浏览器不支持第一种字体，他将尝试下一种字体。
注意: 如果字体系列的名称超过一个字，它必须用引号，如Font Family："宋体"。

多个字体系列是用一个逗号分隔指明：`p{font-family:"Times New Roman", Times, serif;}`。
对于较常用的字体组合，看看 Web安全字体组合`https://www.runoob.com/cssref/css-websafe-fonts.html`。

### 字体样式

主要是用于指定斜体文字的字体样式属性。这个属性有三个值：

* 正常 - 正常显示文本
* 斜体 - 以斜体字显示的文字
* 倾斜的文字 - 文字向一边倾斜

```css
p.normal {font-style:normal;}
p.italic {font-style:italic;}
p.oblique {font-style:oblique;}
```

### 字体大小

font-size 属性设置文本的大小。字体大小的值可以是绝对或相对的大小。
绝对大小：

* 设置一个指定大小的文本
* 不允许用户在所有浏览器中改变文本大小
* 确定了输出的物理尺寸时绝对大小很有用

相对大小：

* 相对于周围的元素来设置大小
* 允许用户在浏览器中改变文字大小

如果不指定一个字体的大小，默认大小和普通文本段落一样，是16像素（16px=1em）。

```html
<style>
    .c1{
        /*对应的是rgb颜色*/
        color: #00FF7F;
        font-size: 58px;
        /*加粗*/
        font-weight: 600;
        font-family: Microsoft Yahel;
    }
</style>
```

## 高度和宽度

```html
<style>
    .c1{
        display: inline-block;
        height: 300px;
        width: 500px;
        border: 1px solid red;
        /*宽度也支持百分比：width:50%;*/
        /*使文本水平方向居中*/
        text-align: center;
        /*使文本垂直方向居中，值与高度的值相等*/
        line-height: 300px;
    }
</style>
<span class="c1">中国</span>
<span class="c1">联通</span>
/*将块级标签转换为行内标签*/
<div style="display: inline;">中国</div>
/*将行内标签转换为块级标签*/
<span style="display: block;">联通</span>
```

注意事项：

* 高度与宽度的设置对行内标签默认无效；对块级标签默认有效。
* `display: inline-block` 使其既具有块级标签的优势，又具有行级标签优势。

## 浮动

```html
<div>
    <span>左边</span>
    <--使文字靠右对齐-->
    <span style="float: right">右边</span>
</div>
```

当块级标签应用了浮动效果，它将不再独占一行，而是自己有多大就占用多大的空间。

```html
<head>
    <style>
        .item{
            float: left;
            width: 288px;
            height:178px;
            border: 1px solid red;
        }
    </style>
</head>
<body>
    <div>
        <--这里的四个盒子会在同一行排列-->
        <div class="item"></div>
        <div class="item"></div>
        <div class="item"></div>
        <div class="item"></div>
        <--清除浮动元素带来的脱离文档流的影响-->
        <div style="clear: both;"></div>
    </div>
</body>
```

## 边距

1. 内边距：使用`padding`在元素内部设置边距，内部增大
2. 外边距：使用`margin`设置与外部元素的距离

```html
<head>
    <style>
        body {
            margin: 0;
        }
        .inter{
            width: 200px;
            height:150px;
            border: 1px solid red;
            /*使元素内部的元素与边框保持距离*/
            padding-top:20px;
            padding-right:20px;
            padding-bottom:20px;
            padding-left:20px;
            /*当需要设置四边边距一样时，可以简写成这样*/
            padding:20px;
            /*顺时针方向设置边距：上右下左*/
            padding: 20px 10px 5px 20px;
        }
        .container{
            width: 1226px;
            /*区域居中*/
            margin: 0 auto;
        }
    </style>
</head>
<body>
    <div class="inter">
        <div>听妈妈的话</div>
        <div>小朋友你是否有很多问号</div>
    </div>
    <div class="container">
        <div style="height: 200px; background-color: blue;"></div>
        <div style="height: 100px; background-color: red; margin-top:20px;"></div>
    </div>
</body>
```

## after

`:after` 选择器向选定元素的最后子元素后面插入内容。

```html
<head>
    <style>
        .clearfix:after {
            content: "";
            display: block;
            clear: both;
        }
        .item {
            float: left;
        }
    </style>
</head>
<body>
    <div class="clearfix">
        <div class="item"></div>
        <div class="item"></div>
        <div class="item"></div>
    </div>
</body>
```

## 定位（position）

position 属性指定了元素的定位类型。position 属性的五个值：static、relative、fixed、absolute、sticky。元素可以使用的顶部（top），底部(bottom)，左侧(left)和右侧(right)属性定位。然而，这些属性无法工作，除非是先设定position属性。它们也有不同的工作方式，这取决于定位方法。

### static 定位

HTML元素的默认值，即没有定位，遵循正常的文档流对象。
静态定位的元素不会受到top/bottom/left/right的影响。

```css
div.static {
    position: static;
    border: 3px solid #73AD21;
}
```

### fixed

元素的位置相对于浏览器窗口是固定位置。即使窗口是滚动的它也不会移动。

```css
/*回到顶部按钮样式*/
.back {
    position: fixed;
    width: 60px;
    height: 60px;
    border: 1px solid red;
    right: 10px;
    bottom: 50px;
}

/*登录框样式*/
.dialog {
    position: fixed;
    height: 300px;
    width: 500px;
    background-color: white;
    /*使登录框保持水平居中*/
    left: 0;
    right: 0;
    margin: 0 auto;
    top: 200px;
}
.mask {
    background-color: black;
    position: fixed;
    left: 0;
    right: 0;
    top: 0;
    bottom: 0;
    opacity: 0.7;
    /*针对fixed元素设置图层顺序，z-index值大的在最前*/
    z-index: 3;
}
```

```html
<body>
    /*常见的登录时的页面往往有三个图层，最底层为原始网页，其上是一层mask，对其进行遮罩，避免影响用户登录或注册，最上层才是登录框。*/
    <div style="height: 1000px">原始网页</div>
    <div class="mask"></div>
    <div class="dialog"></div>
</body>
```

Fixed定位使元素的位置与文档流无关，因此不占据空间。
Fixed定位的元素和其他元素重叠。

### relative 和 absolute 定位

**relative**：相对定位元素，指将元素相对于其默认位置进行定位。在 relative 定位中，元素会保持其在文档流中的位置，但它的位置可以通过修改 top、bottom、left 或 right 属性进行微调。如果这些属性被设置为一个非零的值，则元素将相对于其默认位置移动，在视觉上改变元素的位置。此时，其他元素的位置不会受到影响。
**absolute**：绝对定位元素，指将元素相对于其祖先元素中的某个位置进行定位。在 absolute 定位中，元素的位置完全脱离了文档流，它会根据它的祖先元素设置的定位进行移动，通常是相对于最近的已定位的祖先元素。如果没有找到已定位的祖先元素，则它将相对于浏览器的窗口进行定位。设置 top、bottom、left 或 right 属性会改变元素的位置，但其他元素的位置也会受到影响。因此，absolute 定位通常用于创建悬浮组件、覆盖层和下拉菜单等 UI 元素。

```html
<style>
    .c1 {
        height: 300px;
        width: 500px;
        border: 1px solid red;
        margin: 100px;
        position: relative;
    }
    .c1 .c2 {
        height: 59px;
        width: 59px;
        background-color: #FFF;
        position: absolute;
        right: 20px;
        bottom: 10px
    }
</style>
<body>
    <div class="c1">
        <div class="c2"></div>
    </div>
</body>
```

### sticky 定位

## 边框

```css
.c1 {
    height: 50px;
    width: 200px;
    margin: 100px;
    background-color: #333;
    /*先添加透明边框，使效果不突兀*/
    border-left: 2px solid transparent;
}
.c1:hover {
    border-left: 2px solid red;

}
```

## 小结

1. body标签会自带边距，如果需要完全填充可以使用`margin: 0;`来设置
2. 内容居中
   1. 文本居中：`<div style="width: 200px; text-align: center;">文本</div>`
   2. 区域居中：`<div style="width: 300px; margin: 0 auto;">区域</div>`
3. 如果父元素没有高度或宽度，它会被子元素的高度和宽度支撑起来。
4. 如果存在浮动，需要在浮动元素的同级末尾添加`<div style="clear: both"></div>`
5. 行内标签的高度、内外边距，默认无效。
6. 垂直方向居中：
   1. 文本：`line-height`；
   2. 图片/块：边距：`pedding`。
7. 去除a标签默认的下划线：`text-decoration: none;`。
8. hover：鼠标移动到该标签所显示的样式，使用`.classname:hover{}`来定义。
9. 设置透明度：`opacity:0.5;`，值为：[0-1]。
