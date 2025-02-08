# HTML

## 初识

```html
<h1>一级标题</h1>
<div>块级标签，独自占一行</div>
<span>行内标签/内联标签，自己有多大就占多少空间</span>
<a href="www.baidu.com">超链接</a>
<img src="https://pic1.zhimg.com/v2-18f0e8f9aa049843a2f1ea1d2712933e_r.jpg" style="height: 50px;" alt="图片说明" title="鼠标悬停时的文字说明">
<ul>
    <li>无序列表行1</li>
    <li>无序列表行2</li>
    <li>无序列表行3</li>
</ul>
<ol>
    <li>有序列表行1</li>
    <li>有序列表行2</li>
    <li>有序列表行3</li>
</ol>
<table>
    <thead><tr><th>th表格表头，tr表行，td表单元格</th></tr></thead>
    <tbody><tr><td>表格数据</td></tr></tbody>
</table>
<form method="post" action="/success">
    <h2>表单</h2>
    <div>
        用户名：<input type="text" name="user" />
    </div>
    <div>
        密码：<input type="password" name="password" />
    </div>
    <div>
        <input type="radio" name="gender" value="1">男
        <input type="radio" name="gender" value="0">女
    </div>
    <div>
        爱好：
        <input type="checkbox" name="hobby" value="10">篮球
        <input type="checkbox" name="hobby" value="20">足球
        <input type="checkbox" name="hobby" value="30">排球
        <input type="checkbox" name="hobby" value="40">乒乓球
    </div>
    <div>
        城市：
        <select name="city" id="">
            <option value="bj">北京</option>
            <option value="sh">上海</option>
            <option value="sz">深圳</option>
        </select>
    </div>
    <div>
        擅长：
        <select name="skill" id="" multiple>
            <option value="100">docker</option>
            <option value="101">k8s</option>
            <option value="102">shell</option>
        </select>
    </div>
    <div>
        <textarea name="more" id="" cols="30" rows="3">备注</textarea>
    </div>
    <input type="submit" value="提交">
</form>
```

form表单 + input/select/textarea 数据框
    action，提交地址
    method，提交方式
    form标签中有一个submit
    内部标签都需要设置name属性

在新标签页打开页面使用`target="_blank"`，如：
`<a href="/depart/add" class="btn btn-primary" target="_blank">新建部门</a>`