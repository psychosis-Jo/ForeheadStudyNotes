# JavaScript

## Javascript 简介

JavaScript 是脚本语言
JavaScript 是一种轻量级的编程语言。
JavaScript 是可插入 HTML 页面的编程代码。
JavaScript 插入 HTML 页面后，可由所有的现代浏览器执行。

### 要学的内容

Javascript 直接写入HTML输出流
Javascript 对事件的反应
Javascript 改变HTML内容
Javascript 改变HTML图像
Javascript 改变HTML样式
Javascript 验证输入

### JavaScript 用法

HTML 中的 Javascript 脚本代码必须位于 `<script>` 与 `</script>` 标签之间。
`<script>`可被放置在 HTML 页面的 `<body>` 和/或 `<head>` 部分中，推荐放在`<body>`中。可以直接包裹JavaScript代码，也可以把代码保存在外部的文件中，使用`src`属性引入代码。

```html
<!DOCTYPE html>
<html>
    <head>
        <script src="myScript.js"></script>
        <script>
            //第一个函数
            function myFunction()
            {
                document.getElementById("demo").innerHTML="我的第一个 JavaScript 函数";
            }
        </script>
    </head>
    <body>
        <script src="myScript_1.js"></script>
        <button type="button" onclick="myFunction()">尝试一下</button>
    </body>
</html>
```

### JavaScript 函数和事件

JavaScript 语句会在页面加载时执行。
通常，需要在某个事件发生时执行代码，比如当用户点击按钮时。
如果把 JavaScript 代码放入函数中，就可以在事件发生时调用该函数。

### DOM (文档对象模型)

```javascript
//根据id获取标签
var tag = document.getElementById("txt");
//获取标签中的文本
tag.innerText
//修改标签中的文本
tag.innerText = "修改后";

//创建标签
var tag1 = document.creatElement("div");
//在标签里填写内容
tag1.innerText = "值1"
```

```html
<ul id="city">

</ul>
<script>
    // 定位id=city的标签里，DOM
    var parentTag = document.getElementById("city");

    //创建 <li>北京</li>
    var tag = document.createElement("li");
    tag.innerText = "北京";

    //在id=city的标签里添加创建好的元素
    parentTag.appendChild(tag);
</script>
```

#### 事件

### BOM 定时器

### jQuery

#### jQuery使用

jQuery是Javascript的一个第三方类库。在jQuery的基础上有很多现成的工具可以直接使用，如Bootstrap的动态效果；也可以基于jQuery自己开发一个功能。

1. 下载：`https://code.jquery.com/jquery-3.7.0.min.js`
2. 将下载的js文件放到项目js文件的存放目录，如 `static/js/`下；
3. 在HTML中的body底部使用`script`标签引入该js文件。
4. 直接定位标签（和css中的选择器一样）：
   * ID选择器：`<h1 id="txt">中国联通</h1>` `$("#txt")`
   * 类选择器：`<h1 class="c1">中国联通</h1>` `$(".c1")`
   * 标签选择器：`<h1>中国联通</h1>` `$("h1")`
   * 层级选择器：

        ```html
        <h1 class="c1">标题1</h1>
        <h1 class="c1">
            <div class="c2">
                <span></span>
                <a>标题2</a>
            </div>
        </h1>
        <h1 class="c2">标题3</h1>
        <script src="../static/js/jquery-3.7.0.min.js"></script>
        <script>
            $(".c1 .c2 a")
        </script>
        ```

   * 多选择器：

        ```html
        <h1 class="c1">标题1</h1>
        <h1 class="c1">
            <div class="c2">
                <span></span>
                <a>标题2</a>
            </div>
        </h1>
        <h1 class="c2">标题3</h1>
        <ul>
            <li>行1</li>
            <li>行2</li>
         </ul>
        <script src="../static/js/jquery-3.7.0.min.js"></script>
        <script>
            $(".c1, .c2, li")
        </script>
        ```

   * 属性选择器：`<input type="text" name="n1">` `$("input[name='n1']");`
5. 间接定位标签：
   * 定位同级标签：

        ```html
        <div>
            <div>上海</div>
            <div id="c3">广州
                <div>白云区</div>
                <div id="TianHe">天河区</div>
                <div>番禺区</div>
            </div>
            <div>深圳</div>
            <div>北京</div>
        </div>
        <script src="../static/js/jquery-3.7.0.min.js"></script>
        <script>
            $("#c3"); //定位该标签
            $("#c3").prev; //定位该标签同级的上一个标签
            $("#c3").next(); //定位该标签同级的下一个标签
            $("#c3").next().next(); //定位该标签同级下一个标签的下一个标签
            $("#c3").siblings(); //定位该标签同级的所有标签
        </script>
        ```

   * 定位不同层级标签

        ```html
        <div>
            <div>上海</div>
            <div id="c3">广州
                <div>白云区</div>
                <div id="TianHe">天河区</div>
                <div>番禺区</div>
            </div>
            <div>深圳</div>
            <div>北京</div>
        </div>
        <script src="../static/js/jquery-3.7.0.min.js"></script>
        <script>
            $("#c3").parent();  //找父标签
            $("#c3").parent().parent(); //找父标签的父标签
            $("#c3").children(); //找所有子标签
            $("#c3").children("#TianHe");  //在所有子标签中找id=TianHe的
            $("#c3").find("#TianHe"); //在所有层级的子标签中找id=TianHe的
        </script>
        ```

6. 操作样式：
   * `addClass()` 添加样式
   * `removeClass()` 去掉样式
   * `hasClass()` 判断是否有该样式
7. 值的操作：

    ```html
    <div id="c1">内容</div>
    <input type="text" id="c2" />
    <script src="../static/js/jquery-3.7.0.min.js"></script>
    <script>
        $("#c1").text();  //获取文本内容
        $("#c1").text("休息");  //设置文本内容
        $("#c2").val();  //获取用户输入的内容
        $("#c2").val("1");  //设置用户输入的内容
    </script>
    ```

8. 事件

    ```html
    <ul>
        <li>百度</li>
        <li>谷歌</li>
        <li>夸克</li>
    </ul>
    <div id="c1">内容</div>
    <script src="../static/js/jquery-3.7.0.min.js"></script>
    <script>
        $(function(){
            //默认当整个页面执行完成才执行javascript代码
            //使用$(function(){}后，当页面的框架加载完成后就开始执行
            $("li").click(function(){
                // 点击li标签时，自动执行这个函数
                // $(this)，只对当前点击的标签有效
                $(this).remove();
            });
            //删除id=c1的标签
            $("#c1").remove();
        });
    </script>
    ```

### 不同函数中this的值

```javascript
function x1(){
    console.log(this);
}
x1(); //这里的this是window

x2 = {
    name: "张三",
    f:function (){
        console.log(this);
    }
}
x2.f(); // 这里的this是x2

x3 = {
    name: "张三",
    f:function (){
        function inner(){
            console.log(this);
        }
        inner();
    }
}
x3.f(); //这里的this是window

x4 = {
    name: "张三",
    f:function (){
        inner = () => {
            console.log(this);
        }
        inner();
    }
}
x4.f(); //箭头函数自己没有this，而是直接使用上级函数的this，因此这里的this是x4
```
