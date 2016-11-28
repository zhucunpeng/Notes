#**Css概念**
>CSS 指层叠样式表 (Cascading Style Sheets)(级联样式表)
Css是用来美化html标签的，相当于页面化妆。

##1、样式书写位置
###1.1 内嵌式写法
```
<head>
    <style type=”text/css”>
    样式表内容
    </style>
</head>
```
* 特点:样式只作用于当前文件，没有真正实现结构表现分离
###1.2 外链式写法
```
<link rel=”stylesheet” href=”1.css”>
```
* 特点：作用范围是当前站点，谁调用谁生效，范围广，真正实现结构表现分离
###1.3行内样式表
```
<div style=”font-size:20px;”></div>
```
* 特点：作用范围仅限于当前标签，范围小，结构表现混在一起。不推荐使用
##2、选择器
> **写法**
选择器{属性:值； 属性:值;}
属性    解释
Width:20px; 宽
Height:20px; 高
Background-color:red; 背景颜色
font-size:24px; 文字大小
text-align:left | center| right 内容的水平对齐方式
text-indent:2em; 首行缩进
Color:red; 文字颜色

### 2.1 基础选择器   
>标签{属性：值;}

* 特点:标签选择器定义之后，会将页面素有的元素都执行这个标签样式

* 颜色的显示方式
 * 直接写颜色的名称
 * 十六进制显示颜色 0-9 a-f #000000 前2位代表红色，中间位代表绿色，后边2位代表蓝色，如#229900可以直接简写#290
 * color:rgb(120,120,120)
 * color:rgba(100,100,100,0.5) A 代表alpha 不透明度 值0-1?
###2.2类选择器（重点） 
>.自定义类名{属性:值; 属性:值；}

* 特点
 * 谁调用，谁生效。
 * 一个标签可以调用多个类选择器。
 * 多个标签可以调用同一个类选择器。
* 命名规则
 * 不能用纯数字或者数字开头来定义类名
 * 不能使用特殊符号或者特殊符号开头（_）来定义类名
 * 不建议使用汉字来定义类名
 * 不推荐使用属性或者属性的值来定义类名
* 常用短语
头:header;内容:content/container;尾:footer;导航:nav;侧栏:sidebar;栏目:column;页面外围控制整体布局宽度:wrapper;左右中:left|right|center;登录条:loginbar;标志:logo;广告:banner;页面主体:main;热点:hot;新闻:news;下载:download;子导航:subnav;菜单:menu;子菜单:submenu;搜索:search;友情链接:firendlink;页脚:footer;版权:copyright;滚动:scroll;内容:content
###2.3ID选择器      
>#自定义名称{属性:值;}

* 特点
 * 一个ID选择器在一个页面只能调用一次。如果使用2次或者2次以上，不符合w3c规范，JS调用会出问题。
 * 一个标签只能调用一个ID选择器。
 * 一个标签可以同时调用类选择器和ID选择器。
###2.4 通配符选择器
> *{属性:值;}
* 特点
 * 给所有的标签都使用相同的样式。
 ★不推荐使用，增加浏览器和服务器负担
##3、复合选择器
>概念两个或者两个以上的基础选择器通过不同的方式连接在一起。
###3.1 交集选择器    
> 标签+类（ID）选择器{属性：值；}

* 特点：
即要满足使用了某个标签，还要满足使用了类（id）选择器。  
###3.2 后代选择器    
>选择器+空格+选择器{属性：值;}

* 特点：
 * 后代选择器首选要满足包含（嵌套）关系。
 * 父集元素在前边，子集元素在后边。
 * 无限制隔代。
 * 只要能代表标签，标签、类选择器、ID选择器自由组合。
###3.3 子代选择器    
>选择器>选择器{属性:值;}

* 特点：
选中直接下一代元素。
###3.4 并集选择器    
> 选择器+，+选择器+，选择器{属性:值;}

###3.5 属性选择器    
>选择器[属性];

```input[type=text]{
} ```

##4、文本元素
###4.1  属性
>font-size:16px; 文字大小
Font-weight: 700 ; 值从100-900，文字粗细，不推荐使用font-weight:bold;
Font-family:微软雅黑; 文本的字体
Font-style: normal | italic; normal 默认值 italic 斜体
line-height: 行高

###4.2 文本属性连写
>font: font-style font-weight font-size/line-height font-family;
注意：font:后边写属性的值。一定按照书写顺序。
文本属性连写文字大小和字体为必写项。

###4.3 文字的表达方式
* 直接写中文名称
font-family:微软雅黑
写字体的英文名称

* font-family:microsoft yahei
* unicode编码
 * 宋体 simsun \5B8B\4F53
 * 黑体 simhei \9ED1\4F53
 * 微软雅黑 microsoft yahei \5FAE\8F6F\96C5\9ED1
 * 浏览器中查找unicode 编码方法:
     * 第一步：F12
     * 第二步：找到console
     * 第三步：输入escape(“宋体”) 注意英文的括号和双引号。
