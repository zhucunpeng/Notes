#**Css概念**
>CSS 指层叠样式表 (Cascading Style Sheets)(级联样式表)
Css是用来美化html标签的，相当于页面化妆。
 
##1、定位 position
>定位方向: left | right | top | bottom
###1.1 position:static； 静态定位
>默认值，就是文档流。
###1.2 Position:absolute;  绝对定位
特点：

* 元素使用绝对定位之后不占据原来的位置（脱标）
* 元素使用绝对定位，位置是从浏览器出发。
* 嵌套的盒子，父盒子没有使用定位，子盒子绝对定位，子盒子位置是从浏览器出发。
* 嵌套的盒子，父盒子使用定位，子盒子绝对定位，子盒子位置是从父元素位置出发。
* 给行内元素使用绝对定位之后，转换为行内块。（不推荐使用，推荐使用display:inline-block;）

###1.3 Position: relative;  相对定位
特点：

* 使用相对定位，位置从自身出发。
* 还占据原来的位置。
* 子绝父相（父元素相对定位，子元素绝对定位）
* 嵌套的盒子，父元素相对定位，子元素绝对定位，子元素从父元素出发设置自身位置。
* 行内元素使用相对定位不能转行内块
### 1.4 Position:fixed;   固定定位
特点：

* 固定定位之后，不占据原来的位置（脱标）
* 元素使用固定定位之后，位置从浏览器出发。
* 元素使用固定定位之后，会转化为行内块（不推荐，推荐使用display:inline-block;）
##2、定位盒子居中显示
*  margin:0 auto; 只能让标准流和盒子居中对齐
* 定位的盒子居中:
先往右走父元素盒子的一半50%，在向左走子盒子的一半(margin-left:负值）
```
.nav{
width: 960px;
height: 60px;
background:#666;
position: absolute;
bottom:0;
left:50%;
margin-left:-480px;
}
```
##3、标签包含规范
* div可以包含所有的标签。
* p标签不能包含div h1等标签。
* h1可以包含p，div等标签。
* 行内元素尽量包含行内元素，行内元素不要包含块元素。

##4、规避脱标流
* 尽量使用标准流。
* 标准流解决不了的使用浮动。
* 浮动解决不了的使用定位。

##5、图片和文字垂直居中对齐
>vertical-align 对inline-block最敏感，

默认属性是：vertical-aligin:baseline;

* baseline 默认，元素防止在父元素的基线上
* sub 垂直对齐文本的下标
* super 垂直对齐文本的上标
* top 把元素的顶端与行中最高元素的顶端对齐
* text-top 把元素的顶端与父元素的字体的顶端对齐
* middle 把此元素放置在父元素的中部
* bottom 把元素的顶端与行中最低的元素的顶端对齐
* text-bottom 把元素的低端与都元素字体的低端对齐
* length % 使用line-height 属性的百分比值来排列此元素 允许使用负值
* length inherit 规定应该从父元素继承vertical-align属性的值
```img{
图片和文字垂直居中对齐
vertical-align:middle;
}
```

##6、css可见性
* overflow:hidden; 溢出隐藏
* visibility:hidden; 隐藏元素 隐藏之后还占据原来的的位置
* display:none; 隐藏元素 隐藏之后不占据原来的位置
* display:block; 元素可见
* display:none和display:block; 常配合js使用

##7、CSS之内容移除(网页优化)
* 使用text-indent:-5000em;
```a{
text-indent:-5000em;
}```
* 将元素高度设置为0，使用内边距将盒子撑开，给盒子使用overflow:hidden;将文字隐藏
```.box{
width:300px;
height:0;
padding-top:100px;
overflow:hidden;
background:red;
}```

## 8、精灵图 Sprites
###8.1 优点
1、利用CSS Sprites能很好地减少了网页的http请求，从而大大的提高了页面的性能，这也是CSS Sprites最大的优点，也是其被广泛传播和应用的主要原因。
2、个人认为能CSS Sprites能减少图片的字节，我曾经比较过多次3张图片合并成1张图片的字节总是小于这3张图片的字节总和。
###8.2 Sprites缺点
 **诚然CSS Sprites是如此的强大，但是也存在一些不可忽视的缺点**
1、在图片合并的时候，你要把多张图片有序的合理的合并成一张图片，还要留好只够的空间，防止板块内不会出现不必要的背景；这些还好，做痛苦的是在宽屏，高分辨率的屏幕下的自适应页面，你的图片如果不够宽，很容易出现背景断裂；
2、CSS Sprites在开发的时候比较麻烦，你要通过photoshop或其他工具测量计算每一个背景单元的精确位置，这是针线活，没什么难度，但是很繁琐；幸好腾讯的鬼哥用RIA开发了一个CSS Sprites 样式生成工具，虽然还有一些使用上的不灵活，但是已经比photoshop测量来的方便多了，而且样式直接生成，复制，拷贝就OK！
3、CSS Sprites在维护的时候比较麻烦，如果页面背景有少许改动，一般就要改这张合并的图片，无序改的地方最好不要动，这样避免改动更多的css，如果在原来的地方放不下，有只能（最好）往下加图片，这样图片的字节就增加了，还要改的css。


 
 
 