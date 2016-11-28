#**Css概念**
>CSS 指层叠样式表 (Cascading Style Sheets)(级联样式表)
Css是用来美化html标签的，相当于页面化妆。
##1、页面布局
###1.1 文档流(标准流)
>元素自上而下，自左而右，块元素独占一行，行内元素在一行上显示，碰到父集元素的边框换行。
###1.2 浮动布局
>float:  left | right
特点：
★元素浮动之后不占据原来的位置（脱标）
★浮动的盒子在一行上显示
★行内元素浮动之后转换为行内块元素。（不推荐使用，转行内元素最好使用display: inline-block;）
###1.3清除浮动
>当父容器没有设置高度，里面的盒子没有设置浮动的情况下会将父容器的高度撑开。一旦父容器中的盒子设置浮动，脱离标准文档流，父容器立马没有高度，下面的盒子会跑到浮动的盒子下面。出现这种情况，我们需要清除浮动

* 清除浮动不是不用浮动，清除浮动产生的不利影响。
* 清除浮动的方法
clear: left  |  right  | both
工作里用的最多的是clear:both;
 * 额外标签法
    在最后一个浮动元素后添加标签。
    ```<div style="clear:both;"></div>```
 * 给父级元素使用overflow:hidden;
 * 伪元素清除浮动  推荐使用
```
.clearfix:after{
    content:".";
    display: block;
    height: 0;
    line-height: 0;
    visibility: hidden;
    clear:both;
}
/*兼容ie浏览器*/
.clearfix{
    zoom:1;
}
```
### 1.4 overflow
* overflw:hidden; 会将出了盒子的内容裁掉
* overflw:auto;当内容出了盒子之外，会自动生成滚动条，如果没有内容出盒子之外，则不出现滚动条
* overflw:scroll;不管你内容有没有出盒子，都会生成滚动条
* overflw:visible;内容出了盒子会显示，不生成滚动条

##2、CSS初始化
###2.1腾讯：
```
body,ol,ul,h1,h2,h3,h4,h5,h6,p,th,td,dl,dd,form,fieldset,legend,input,textarea,select{margin:0;padding:0} 
body{font:12px"宋体","Arial Narrow",HELVETICA;background:#fff;-webkit-text-size-adjust:100%;} 
a{color:#2d374b;text-decoration:none} 
a:hover{color:#cd0200;text-decoration:underline} 
em{font-style:normal} 
li{list-style:none} 
img{border:0;vertical-align:middle} 
table{border-collapse:collapse;border-spacing:0} 
p{word-wrap:break-word} 
```
###2.2新浪：
```
body,ul,ol,li,p,h1,h2,h3,h4,h5,h6,form,fieldset,table,td,img,div{margin:0;padding:0;border:0;} 
body{background:#fff;color:#333;font-size:12px; margin-top:5px;font-family:"SimSun","宋体","Arial Narrow";}
ul,ol{list-style-type:none;} 
select,input,img,select{vertical-align:middle;} 
a{text-decoration:none;} 
a:link{color:#009;} 
a:visited{color:#800080;} 
a:hover,a:active,a:focus{color:#c00;text-decoration:underline;} 
```

###2.3淘宝：
```
body, h1, h2, h3, h4, h5, h6, hr, p, blockquote, dl, dt, dd, ul, ol, li, pre, form, fieldset, legend, button, input, textarea, th, td { margin:0; padding:0; } 
body, button, input, select, textarea { font:12px/1.5tahoma, arial, \5b8b\4f53; } 
h1, h2, h3, h4, h5, h6{ font-size:100%; } 
address, cite, dfn, em, var { font-style:normal; } 
code, kbd, pre, samp { font-family:couriernew, courier, monospace; } 
small{ font-size:12px; } 
ul, ol { list-style:none; } 
a { text-decoration:none; } 
a:hover { text-decoration:underline; } 
sup { vertical-align:text-top; } 
sub{ vertical-align:text-bottom; } 
legend { color:#000; } 
fieldset, img { border:0; }
button, input, select, textarea { font-size:100%; } 
table { border-collapse:collapse; border-spacing:0; } 
```
 