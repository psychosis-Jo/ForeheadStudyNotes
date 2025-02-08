# BootStrap

## 简介&使用

Bootstrap 是全球最受欢迎的**前端组件库**，用于开发响应式布局、移动设备优先的 WEB 项目。
Bootstrap5 目前是 Bootstrap 的最新版本，是一套用于 HTML、CSS 和 JS 开发的开源工具集。它支持 Sass 变量和 mixins、响应式网格系统、大量的预建组件和强大的 JavaScript 插件，助你快速设计和自定义响应式、移动设备优先的站点。
移动设备优先策略：
    内容：决定什么是最重要的
    布局：优先设计更小的宽度；基础的CSS是移动设备优先，媒体查询是针对平板电脑、台式电脑
    渐进增强：随着屏幕大小的增加而添加元素

1. 下载
   1. 目前Bootstrap的最新版本为v5，功能最新也最全面，而需要兼容低版本浏览器则需使用v3。
   2. Bootstrap v3下载：`https://github.com/twbs/bootstrap/releases/download/v3.4.1/bootstrap-3.4.1-dist.zip`
   3. Bootstrap v4下载：`https://github.com/twbs/bootstrap/releases/download/v4.6.2/bootstrap-4.6.2-dist.zip`
   4. Bootstrap v5下载：`https://github.com/twbs/bootstrap/releases/download/v5.3.0-alpha1/bootstrap-5.3.0-alpha1-dist.zip`
2. 部署：下载解压后，将整体文件夹放置到项目的static/plugins目录下
3. 引入：在html头部使用`link`标签进行引入
   1. 开发环境引入：`<link rel="stylesheet" href="../static/plugins/bootstrap-3.4.1/css/bootstrap.css">`
   2. 生产环境引入：`<link rel="stylesheet" href="../static/plugins/bootstrap-3.4.1/css/bootstrap.min.css">`
4. 使用：vscode安装插件`IntelliSense for CSS class names in HTML`或`HTML CSS Support`可以在编写html页面的class类名时，提示引入文件中已经编写好的样式，根据需要和提示进行选择补全即可。

## 全局CSS样式

### 栅格系统（Grid System）

`https://v3.bootcss.com/css/#grid`

Bootstrap提供了一套响应式、移动设备优先的流式栅格系统，随着屏幕或视口（viewport）尺寸的增加，系统会自动分为最多**12**列。它包含了用于简单的布局选项的预定义类，也包含了用于生成更多语义布局的功能强大的混合类。可以通过类前缀+格数（col-xs-[6]）来设置元素所占用的空间。

#### 栅格系统工作原理

栅格系统通过一系列包含内容的 行 和 列 来创建页面布局。下面列出了 Bootstrap 网格系统是如何工作的：

1. “行（row）”必须包含在 `.container` （固定宽度）或 `.container-fluid` （100% 宽度）中，以便为其赋予合适的排列（aligment）和内补（padding）。
2. 通过“行（row）”在水平方向创建一组“列（column）”。
3. 你的内容应当放置于“列（column）”内，并且，只有“列（column）”可以作为行（row）”的直接子元素。
4. 类似 `.row` 和 `.col-xs-4` 这种预定义的类，可以用来快速创建栅格布局。Bootstrap 源码中定义的 mixin 也可以用来创建语义化的布局。
5. 通过为“列（column）”设置 `padding` 属性，从而创建列与列之间的间隔（gutter）。通过为 `.row` 元素设置负值 `margin` 从而抵消掉为 `.container` 元素设置的 `padding`，也就间接为“行（row）”所包含的“列（column）”抵消掉了`padding`。
6. 负值的 `margin`就是下面的示例为什么是向外突出的原因。在栅格列中的内容排成一行。
7. 栅格系统中的列是通过指定1到12的值来表示其跨越的范围。例如，三个等宽的列可以使用三个 `.col-xs-4` 来创建。
8. 如果一“行（row）”中包含了的“列（column）”大于 `12`，多余的“列（column）”所在的元素将被作为一个整体另起一行排列。
9. 栅格类适用于与屏幕宽度大于或等于分界点大小的设备，并且针对小屏幕设备覆盖栅格类。因此，在元素上应用任何 `.col-md-*` 栅格类适用于与屏幕宽度大于或等于分界点大小的设备，并且针对小屏幕设备覆盖栅格类。因此，在元素上应用任何 `.col-lg-*` 不存在，也影响大屏幕设备。

#### 媒体查询(media query)

媒体查询是"有条件的 CSS 规则"。它只适用于一些基于某些规定条件的 CSS。如果满足那些条件，则应用相应的样式。
Bootstrap 中的媒体查询允许基于视口大小移动、显示并隐藏内容。下面的媒体查询在 LESS 文件中使用，用来创建 Bootstrap 网格系统中的关键的分界点阈值。

```css
/* 超小设备（手机，小于 768px） */
/* Bootstrap 中默认情况下没有媒体查询 */

/* 小型设备（平板电脑，768px 起） */
@media (min-width: @screen-sm-min) { ... }

/* 中型设备（台式电脑，992px 起） */
@media (min-width: @screen-md-min) { ... }

/* 大型设备（大台式电脑，1200px 起） */
@media (min-width: @screen-lg-min) { ... }
```

媒体查询有两个部分，先是一个设备规范，然后是一个大小规则。

```css
/*对于所有带有 min-width: @screen-sm-min 的设备，如果屏幕的宽度小于 @screen-sm-max，则会进行一些处理。*/
@media (min-width: @screen-sm-min) and (max-width: @screen-sm-max) { ... }
```

#### 栅格参数

![栅格参数](bootstrap_img/1_%E6%A0%85%E6%A0%BC%E5%8F%82%E6%95%B0.png)

基本的栅格结构

```html
<div class="container">
   <div class="row">
      <div class="col-*-*"></div>
      <div class="col-*-*"></div>      
   </div>
   <div class="row">...</div>
</div>
<div class="container">....
```

#### 列偏移

使用 `.col-md-offset-*` 类可以将列向右侧偏移。这些类实际是通过使用 `*` 选择器为当前元素增加了左侧的边距（margin）。
例如，`.col-md-offset-4` 类将 `.col-md-4` 元素向右侧偏移了4个列（column）的宽度。

#### 列嵌套

为了使用内置的栅格系统将内容再次嵌套，可以通过添加一个新的 `.row` 元素和一系列 `.col-sm-*` 元素到已经存在的 `.col-sm-*` 元素内。被嵌套的行（row）所包含的列（column）的个数不能超过12（但也不是必须占满12列）。

```html
<div class="row">
  <div class="col-sm-9">
    Level 1: .col-sm-9
    <div class="row">
      <div class="col-xs-8 col-sm-6">
        Level 2: .col-xs-8 .col-sm-6
      </div>
      <div class="col-xs-4 col-sm-6">
        Level 2: .col-xs-4 .col-sm-6
      </div>
    </div>
  </div>
</div>
```

#### 列排序

通过使用 `.col-md-push-*` 和 `.col-md-pull-*` 类就可以很容易的改变列（column）的顺序。其中`*`的范围是从1到11。

```html
<div class="row">
  <div class="col-md-9 col-md-push-3">.col-md-9 .col-md-push-3</div>
  <div class="col-md-3 col-md-pull-9">.col-md-3 .col-md-pull-9</div>
</div>
```

#### Less mixin和变量

除了用于快速布局的预定义栅格类，Bootstrap 还包含了一组 Less 变量和 mixin 用于生成简单、语义化的布局。

##### 变量

通过变量来定义列数、槽（gutter）宽、媒体查询阈值（用于确定合适让列浮动）。我们使用这些变量生成预定义的栅格类。

```css
@grid-columns:              12;
@grid-gutter-width:         30px;
@grid-float-breakpoint:     768px;
```

##### mixin

mixin 用来和栅格变量一同使用，为每个列（column）生成语义化的 CSS 代码。

```css
// Creates a wrapper for a series of columns
.make-row(@gutter: @grid-gutter-width) {
  // Then clear the floated columns
  .clearfix();

  @media (min-width: @screen-sm-min) {
    margin-left:  (@gutter / -2);
    margin-right: (@gutter / -2);
  }

  // Negative margin nested rows out to align the content of columns
  .row {
    margin-left:  (@gutter / -2);
    margin-right: (@gutter / -2);
  }
}
```

### 排版

`https://v3.bootcss.com/css/#type`

## 组件

### 图标

bootstrap本身提供了250 多个来自 Glyphicon Halflings 的字体图标。但如果不够用，可以使用font-awesome的图标。

#### bootstrap 原生图标

出于性能的考虑，所有图标都需要一个基类和对应每个图标的类。把对应的代码放在任何地方都可以正常使用。

注意：

* 为了设置正确的内补（padding），务必在图标和文本之间添加一个空格。
* 不要和其他组件混合使用：图标类不能和其他组件直接联合使用。它们不能在同一个元素上与其它类共同存在。应该创建一个嵌套的`<span>`标签上。
* 只对内容为空的元素起作用：图标类只能应用在不包含任何文本内容或子元素的元素上。
* 改变图标字体文件的位置：Bootstrap 假定所有的图标字体文件全部位于 `../fonts/` 目录内，相对于预编译版 CSS 文件的目录。如果修改了图标字体文件的位置，则需要通过下面列出的任何一种方式来更新 CSS 文件：
  * 在 Less 源码文件中修改 `@icon-font-path` 和/或 `@icon-font-name` 变量。
  * 利用 Less 编译器提供的 相对 URL 地址参数(`http://lesscss.org/usage/#less-options-relative-urls`)。
  * 修改经过编译的 CSS 文件中的 `url()` 路径。
根据自身的情况选择一种方式即可。

#### fontawesome图标

1. 下载
    1. 官网地址：`https://fontawesome.com`，注册、登录后下载`Free For Web`版本。
2. 部署：下载解压后，将整体文件夹放置到项目的static/plugins目录下
3. 引入：在html头部使用`link`标签进行引入
   1. 开发环境：`<link rel="stylesheet" href="../static/plugins/fontawesome-free-6.4.0-web/css/all.css">`；`<link rel="stylesheet" href="../static/plugins/fontawesome-free-6.4.0-web/css/fontawesome.css">`
4. 图标可以通过`font-size`和`color`自定义大小和颜色
   `<i class="fa-sharp fa-solid fa-fire" style="color: gold;font-size: 14px;"></i>`
5. 使用`div`包裹图标，可以为其添加`margin`或`padding`，但如果要使用`float`，则需在父元素中使用`clearfix`类。

    ```html
    <div class="clearfix">
        <div style="display: inline-block; margin-right: 20px;">
            <i class="fa fa-calendar-days" aria-hidden="true"
                style="padding-right: 4px; color: gainsboro;"></i> 2023-06-14
        </div>
        <div style="display: inline-block; margin-right: 20px;">
            <i class="fa fa-user-circle" aria-hidden="true"
                style="padding-right: 4px; color: gainsboro;"></i> 长平
        </div>
        <div style="margin-right: 20px; float: right;">
            <i class="fa fa-comment-dots" aria-hidden="true"
                style="padding-right: 4px; color: gainsboro;"></i> >1000
        </div>
    </div>
    ```

### 导航

### 面板

### 媒体对象

### 分页

## Javascript插件

Bootstrap的动态效果依赖jquery（JavaScript的一个类库），如需使用要先下载并在body底部引入其js文件：

```html
<body>
    <script src="../static/js/jquery-3.7.0.min.js"></script>
    <script src="../static/plugins/bootstrap-3.4.1/js/bootstrap.js"></script>
</body>
```

### 原理

#### data-target属性

要实现动态效果，需要使用 `data-target` 属性来指定一个元素需要应用某种动态效果的目标元素。这个属性通常和Javascript和CSS一起使用，用来定义Web页面上的交互效果。

1. 在 HTML 中定义 `data-target` 属性，该属性可以被赋予任何有效的 CSS 选择器，例如 `#id` 或`.class`。

    ```html
    <button data-target="#my-modal">打开弹窗</button>
    ```

2. 在 JavaScript 中，通过选择器选中 `data-target` 属性所指定的目标元素，并为其添加某种动态效果。例如，我们可以通过 jQuery 来选择特定的元素，然后通过 `.show()` 和 `.fadeOut()` 等函数来控制该元素的显示和隐藏：

    ```javascript
    $("button[data-target='#my-modal']").click(function() {
      $("#my-modal").show();  // 显示目标元素
    });

    $("#close-button").click(function() {
      $("#my-modal").fadeOut();  // 隐藏目标元素
    });
    ```

3. 在 CSS 中，我们可以定义一个与 `data-target` 属性相匹配的 CSS 选择器，并为其添加样式。例如，我们可以使用伪类 `:hover` 来定义鼠标悬停时目标元素的样式：

    ```css
    button[data-target='#my-modal']:hover {
      background-color: #eee;
    }
    ```

通过上述方法，可以在 HTML 页面上实现各种动态效果，例如模态框、下拉菜单、图片轮播等等。

#### data-toggle属性

`data-toggle` 是在 Bootstrap 框架中使用的一个 HTML 属性，用于控制页面上某个元素的状态（比如打开、关闭、切换等）。
一般来说，`data-toggle` 属性和 `data-target` 属性一起使用。`data-toggle` 用来指定触发某个操作的方式（比如点击按钮，或者鼠标悬停等），而 `data-target` 则用来指示需要操作的目标元素。

```html
<!-- 触发打开模态框的按钮 -->
<button type="button" class="btn btn-primary" data-toggle="modal" data-target="#myModal">
  打开模态框
</button>
<!-- 模态框 -->
<div class="modal" id="myModal">
  <div class="modal-dialog">
    <div class="modal-content">
      <!-- 模态框头部 -->
      <div class="modal-header">
        <h4 class="modal-title">Modal Header</h4>
        <button type="button" class="close" data-dismiss="modal">&times;</button>
      </div>
      <!-- 模态框主体 -->
      <div class="modal-body">
        Modal body..
      </div>
      <!-- 模态框底部 -->
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
        <button type="button" class="btn btn-primary">Save changes</button>
      </div>
    </div>
  </div>
</div>
```

上述 HTML 代码中，我们首先定义了一个按钮，并在按钮中使用了 `data-toggle="modal"` 和 `data-target="#myModal"`，分别表示该按钮点击时会触发一个打开模态框的操作，并且该操作的目标元素为 ID 为 "myModal" 的元素。
而在后面的 HTML 中，我们则定义了一个 ID 为 "myModal" 的元素，并且添加了 `class="modal"` 属性，表示该元素是一个模态框。此外，还可以在模态框中添加任意的 HTML 元素作为模态框的内容和样式。
因此，在 Bootstrap 中，`data-toggle` 属性主要用来指示某个元素需要触发什么操作，而 `data-target` 则用来指示该操作所要操作的目标元素。

## 案例

### 登录页

* 宽度+区域居中
* 内边距
* 表单
