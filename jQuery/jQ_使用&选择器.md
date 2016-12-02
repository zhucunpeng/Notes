#**jQ介绍和选择器使用**
## 1. jQuery介绍
### 1.1 jQuery描述（理解）
- jQuery是js的一个库，封装了我们开发过程中常用的一些功能，方便我们来调用，提高了我们的开发效率。
- Js库是把我们常用的功能放到一个单独的文件中，我们用的时候，直接引用到页面里面来就可以了。

### 1.2 主要学习jQuery什么
- 目前这个阶段，主要学习如何来使用jQuery操作DOM，其实就是学习jQuery封装好的那些功能方法，这些方法叫做API（Application Programming Interface应用程序编程接口）。
- 这些API的共同特点是：几乎全都是方法。所以，在使用jQuery的API时，都是方法调用，也就是说要加小括号()，小括号里面是相应的参数，参数不同，功能不同。
### 1.3 版本介绍
- 版本一：1.x版本
- 版本二：2.x版本
- 两个版本的区别：2.x版本，不再支持IE6、7、8
两个版本对浏览器的支持情况：
![](leanote://file/getImage?fileId=58412687334ed27670000006)

## 2 jQuery使用
### 2.1 jQuery的入口函数（重点） 
- jquery的入口函数 1 文档加载完毕 图片不加载的时候就可以执行这个函数
```
$(document).ready(function(){
    alert(1);
})
```

- jquery的入口函数 2 文档加载完毕 图片不加载的时候就可以执行这个函数
```
$(function(){
    alert(1);
});
```

- jquery的入口函数 3 文档加载完毕 图片也加载完毕的时候在执行这个函数
```
$(window).ready(function(){
    alert(1);
})
```

### 2.1 jQuery的入口函数&js入口函数区别
- js入口函数指的是：window.onload = function() {};
- 区别一：书写个数不同
	+ Js入口函数只能出现一次，出现多次会存在事件覆盖的问题。
	+ jQuery的入口函数，可以出现任意多次，并不会存在事件覆盖问题。
- 区别二：执行时机不同
	+ Js入口函数是在所有的文件资源加载完成后，才执行。这些文件资源包括：页面文档、外部的js文件、外部的css文件、图片等。
	+ jQuery的入口函数，是在文档加载完成后，就执行。文档加载完成指的是：DOM树加载完成后，就可以操作DOM了，不用等到所有的外部资源都加载完成。
- 文档加载的顺序：从上往下，边解析边执行。

### 2.3 jQuery的$符号

- js命名规范允许出现的字符有：数字、字母、下划线、$。
  Js命名规范允许作为变量命名开头的字符有：字母、下划线、$；但是，不允许以数字作为变量命名的开头。
- jQuery使用$符号原因：书写简洁、相对于其他字符与众不同、容易被记住。

- 怎么理解jQuery里面的$符号：
$实际上表示的是一个函数。
    + jQuery里面的$函数，根据传入参数的不同，进行不同的调用，实现不同的功能。返回的是jQuery对象

    + jQuery这个js库，除了$之外，还提供了另外一个函数：jQuery
      jQuery函数跟$函数的关系：jQuery ===$;
```
$(); // 调用上面我们自定义的函数$
$(document）.ready(function(){}); // 调用入口函数
$(function(){}); // 调用入口函数
$(“#btnShow”) // 获取id属性为btnShow的元素
$(“div”) // 获取所有的div元素
```

### 2.4 jQuery对象和DOM对象的相互转换（难点）
- DOM对象此处指的是：使用js操作DOM返回的结果。
- jQuery对象此处指的是：使用jQuery提供的操作DOM的方法返回的结果。
jQuery拿到DOM对象后又对其做了封装，让其具有了jQuery方法的jQuery对象，说白了，就是把DOM对象重新包装了一下。
- DOM对象转换成jQuery对象：
```
var $btn1 = $(btn); // 此时就把DOM对象btn转换成了jQuery对象$btn1
$(document）.ready(function(){}); // 调用入口函数
此处是将document这个js的DOM对象，转换成了jQuery对象，然后才能调用jQuery提供的方法：ready
```
- jQuery对象转换成DOM对象：
    + 第一种方式
> 
var btn1 = $btn[0];
此时就把jQuery对象$btn转换成了DOM对象btn1（推荐使用此方式）

    + 第二种方式
> 
var btn2 = $btn.get(0);
此时就把jQuery对象$btn转换成了DOM对象btn2

## 3. jQuery选择器
### 3.1 基本选择器
- #	Id选择器 
```
$(“#btnShow”).css(“color”, “red”);
选择id为btnShow的一个元素（返回值为jQuery对象，下同）
```

- .	类选择器
```
$(“.liItem”).css(“color”, “red”);
选择含有类liItem的所有元素
```

- element	标签选择器	
```
$(“li”).css(“color”, “red”);
选择标签名为li的所有元素
```

### 3.2 层级选择器
- 空格	后代选择器

```
$(“#j_wrap li”).css(“color”, “red”);
选择id为j_wrap的元素的所有后代元素li
```

- >	子代选择器	
```
$(“#j_wrap > ul > li”).css(“color”, “red”);
选择id为j_wrap的元素的所有子元素ul的所有子元素li
```

### 3.3 基本过滤选择器
- :eq(index) 选择匹配到的元素中索引号为index的一个元素，index从0开始	
```
用法：
$(“li:eq(2)”).css(“color”, ”red”);选择li元素中索引号为2的一个元素
```

- :odd 选择匹配到的元素中索引号为奇数的所有元素，index从0开始	

```
用法：
$(“li:odd”).css(“color”, “red”);选择li元素中索引号为奇数的所有元素
```

- :even 选择匹配到的元素中索引号为偶数的所有元素，index从0开始	

```
用法：
$(“li:odd”).css(“color”, “red”);选择li元素中索引号为偶数的所有元素
```

### 3.4 筛选选择器(方法)
- find(selector)	查找指定元素的所有后代元素（子子孙孙）
```
用法：
$(“#j_wrap”).find(“li”).css(“color”, “red”);
选择id为j_wrap的所有后代元素li
```

- children()	查找指定元素的直接子元素（亲儿子元素）	
```
用法：
$(“#j_wrap”).children(“ul”).css(“color”, “red”);
选择id为j_wrap的所有子代元素ul
```

- siblings()	查找所有兄弟元素（不包括自己）	
```
用法：
$(“#j_liItem”).siblings().css(“color”, “red”);
选择id为j_liItem的所有兄弟元素
```

- parent()	查找父元素（亲的）	
```
用法：
$(“#j_liItem”).parent(“ul”).css(“color”, “red”);
选择id为j_liItem的父元素
```
- eq(index)	查找指定元素的第index个元素，index是索引号，从0开始	
```
用法：
$(“li”).eq(2).css(“color”, “red”);
选择所有li元素中的第二个
```



