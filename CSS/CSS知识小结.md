#CSS 基础知识点
##1. 小知识
###1.1   font :  加粗  字号/行高  格式；
* 行高如果不写，默认为父盒子行高；
 * u   ins     下划线
 * i   em      倾斜
 * s   del      删除线
 * font-weight:  normal;         加粗变正常
 * font-style:  normal;           倾斜变正常
 * text-decoration: none;         下划线删除线变正常
 * outline-style: none;           去除蓝色外边框
 * resize:  none;               禁止文本框拖拽
###1.2 模拟鼠标
* cursor: pointer;           鼠标变成小手
* cursor: move;            鼠标变成四角箭头
* cursor: text;             鼠标变成工形插入条光标
* cursor: default;           鼠标变成小白

###1.3 圆角矩形

* border-radius: 宽/高一半；

* border-radius: 50%；

* border-radius: 0.3em；

* border-radius: 左上角  右上角  右下角  左下角；

##2、清除浮动
###2.1 定义阐述
* 问题
父盒子高度为0，子盒子不占位置，子盒子不会撑开父盒子。
（下面的标准流盒子，会跑到父盒子中的子盒子下面。）
* 处理办法
清除浮动。（清除子盒子因为浮动，对父子造成的影响）
* 使用办法
谁出问题给谁加一个clearfix类名。
###2.2 清除浮动的方法
* clear:both;
* overflow: hidden;
* 单伪元素标签法
```
.clearfix:after {
    content: “”;
    height: 0;
    visibility: hidden;
    overflow: hidden;
    dispaly: block;
    clear: both;
}
.clearfix {
    zoom: 1;/*IE678*/
}
```
* 双伪元素标签法
```
.clearfix:before,  .clearfix:after {
    content: “”;
    display: table;
}
.clearfix:after {
    clear: both;
}
.clearfix {
    zoom: 1;/*IE678*/
}
```
###2.3  什么时候用margin和padding（不考虑宽高）

* 需要使用背景图的时候必须用padding。
* 会出现外边距合并或者margin塌陷的时候用padding。
* 行内元素上下只能设置padding，不能设置margin。（行内高16px）
* 看border，如果是a连接，看能不能让字体变色，或者显示小手。
* 看需求。

##3、盒子的问题
###3.1 浮动的盒子
    浮动的盒子比标准流的盒子高，但是能够遮挡住标准流的盒子，遮挡不住里面的图片和文字
###3.2 浮动的盒子相互影响
* 浮动的盒子千万不要让他超出父盒子，超出父盒子的部分会影响下面盒子中的浮动的子盒子
* 撑破盒子和撑开盒子是两回事：撑开盒子变得那么大，撑破盒子还是那么大，子盒子变大，父盒子高度是不变的
###3.3 隐藏盒子问题
* overflow:hidden;  隐藏盒子超出的部分，
* display:none; 隐藏盒子，而且不占位置。(用的最多)
* visibility:hidden;隐藏盒子，而且占位置
* opacity:0; 隐藏盒子而且占位置。
* position/top/;eft/...-999px 隐藏盒子，而且占位置
##4、页面常用知识
###4.1 a链接
* ```<a  href="#">  </a>```    跳到页面顶端
* ```<a  href="  ">  </a>```    相当于刷新
* ```<a href="http://www.2345.com" target="_blank"> </a>```跳转到新的网页
* ```<a href="javascript:void(0);"> </a>``` JS关闭链接的跳转
* ```<a href="javascript:  ;"> </a>``` JS关闭连接的跳转另一种写法

###4.2 权重问题
* left和right
left 比right 权重高，有left又有right 的时候，执行left的值
* top和bottom
top比bottom权重高，有top又有bottom的时候，执行top的值。
###4.3 半透明
* opacity:0.4;
优点方便。缺点：里面的内容也会半透明。
* C3解决半透明
background: rgba(0,0,0,0.3);
background: rgba(0,0,0, .3);
* 定位问题
relative 不能给行内元素设置宽高
定位中 static和relative两个定位不能给行内元素设置宽高，absolute和fixed可以
###4.4 层级的问题
* 总结
标准流盒子低于浮动的盒子，浮动的盒子有地狱定位的盒子
定位高于浮动，浮动高于标准流，高低恶化占不占位置无关(出去static之外)
* 用法
①.必须有定位.(除去static之外)
②.给定z-index的值为层级的值(不给默认为0)
 * 层级为0的盒子,也比标准流和浮动高
 * 层级为负的盒子,比标准流和浮动低
 * 层级不取小数
 * 层级一样,后面的盒子比前面的层级高
 * 浮动或者标准流的盒子,后面的盒子比前面的层级高
* 定位中
absolute是不占位置的，relative是占位置的，层级的高低和占不占位置没有关系