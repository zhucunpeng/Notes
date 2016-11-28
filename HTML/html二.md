#**Hyper text markup language**
>超文本标记语言。超文本：超链接。（实现页面跳转）
 
## 1、<head>内使用一些标签
###1.1 关键字
```html
<meta name="keywords" content="Java培训,Android培训,安卓培训,PHP培训,C++培训,iOS培训,网页设计培训,平面设计培训,UI设计培训,游戏开发培训,移动开发培训,网络营销培训,web前端培训">
```

###1.2 网页描述
```html
<meta name="description" content="传智播客，据说是中国最靠谱的IT培训机构！">
```

###1.3 网页重定向
```html
<meta http-equiv="refresh"  content="5; http://www.itcast.cn">
5秒后自动调转到http://itcast.cn 这个网站
```

###1.4 链接外部样式表文件
```
<link rel="stylesheet" href="1.css">
```

###1.5 icon图标
```
<link rel="icon" href="favicon.ico"> 
```

##2、表格
####2.1 格式
```
<table>    表格
    <tr>       行
        <td></td> 列
        <td></td>
        <td></td>
    </tr>
</table>
```

##2.2 属性
>属性:border="1" 边框,width="100"宽度,height="120"高度,cellspacing="2"单元格与单元格的距离,cellpadding="2"内容距边框的距离,align="left|right|center",bgcolor="red" 背景颜色,

##2.3表头和单元格合并
```
<caption>表头显示</caption>  
colspan="2" 合并同一行上的单元格；rowspan="2"合并同一列上的单元格
```

##2.4 表格标题
```
<th>表格标题</th> 用法和td一样
标题的文字自动加粗水平居中对齐
```

##2.5 边框颜色
>bordercolor="red" 边框的颜色

##2.6 内容垂直对齐方式
>valign="top|middle|bottom"顶部|中间|底部

##2.7 水平对其方式
>align="left|centrer|right" 左边|居中|右边

# 3、表格
## 3.1 表单域
```
<form action="1.php" method="get">   </form>
属性：action 处理信息；method="get|post"
    get 通过地址栏提供(传输)信息，安全性差。
    post 通过1.php 来处理信息，安全性高。
```

##3.2 表单信息分组
```
<form action="1.php" method="post">
    <fieldset>  对表单信息分组
        <legend> 表单信息分组名称</legend>
    </fieldset>
</form>
```

##3.3文本输入框
```
<用户名:<input type="text" maxlength="6" readonly="readonly" disabled="disabled" name="uername" value="大前端">
maxlength="6" 限制输入字符长度
readonly="readonly" 将输入框的设置为只读状态(不能编辑)
disabled="disabled" 输入框未激活状态
name="uername" 输入框的名称
value="大前端" 将输入框的内容传给处理文件
```

##3.4 密码输入框
```
密码:<input type="password" name="pwd">
```

##3.5 单选框
```
<input type="radio" name="gender" checked="checked">男
只有将name的值设置相同的时候，才能实现单选效果 checked="checked" 设置默认选择项
```

##3.6 下拉列表
```
<select>  
    <optgroup label="北京市">
        <option>朝阳区</option>
        <option>昌平区</option>
    </optgrounp>
</select>    下拉列表分组
<select multiple="multiple">  
    <option selected="selected">下拉列表选项</option>
</select>   多选下拉框
属性：
Multiple=”multiple”  将下拉列表设置为多选项
Selected=”selected”  设置默认选中项目
Label=””  分组名称。

```

##3.7 多选框
```html
<input type="checkbox" checked="checked">喝酒
<input type="checkbox"  checked="checked">抽烟
Checked=”checked” 设置默认选中项
```

##3.8 多行文本框
```
<textarea cols="130" rows="10"> </textarea>
cols 控制输入字符的长度
rows 控制输入的行数
```

## 3.9 常用控件按钮
```
文件上传控件  <input type="file">
文件提交按钮  可以实现信息提交功能<input type="submit"> 
普通按钮   不能提交信息，配合JS使用<input type="button" value="普通按钮"> 
图片按钮   图片按钮可以实现信息提交功能<input type="image" src="按钮.jpg"> 
重置按钮  将信息重置到默认状态<input type="reset">﻿​
```

##3.10 html5新增表单控件
```
网址控件 <input type="url">
日期控件<input type="date">
时间控件 <input type="time" 
邮件控件 <input type="email"
数字控件一次跳跃的步数为5<input type="number" step="5">
滑块控件 一次滑动的步数为5<input type="range" step="5"> 
```


 
 