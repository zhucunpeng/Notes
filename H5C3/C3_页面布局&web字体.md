# C3_页面布局&web字体
## 1. 页面布局
### 1.1 伸缩布局
- 定义阐述：
CSS3在布局方面做了非常大的改进，使得我们对块级元素的布局排列变得十分灵活，适应性非常强，其强大的伸缩性，在响应式开中可以发挥极大的作用。
    + 主轴：Flex容器的主轴主要用来配置Flex项目，默认是水平方向
    + 侧轴：与主轴垂直的轴称作侧轴，默认是垂直方向的
    + 方向：默认主轴从左向右，侧轴默认从上到下
    + 主轴和侧轴并不是固定不变的，通过flex-direction可以互换。
- 必要元素：
    + 指定一个盒子为伸缩盒子 display: flex
    + 设置属性来调整此盒的子元素的布局方式 例如 flex-direction
    + 明确主侧轴及方向
    + 可互换主侧轴，也可改变方向
- 各属性详解
    + flex-direction调整主轴方向（默认为水平方向）
    该属性通过定义flex容器的主轴方向来决定felx子项在flex容器中的位置
        * flex-direction:row  水平方向
        * flex-direction:reverse-row   水平翻转
        * flex-direction:column  垂直
        * flex-direction:column-reverse  垂直翻转
    + justify-content调整主轴(横轴)对齐
        * justify-content 设置或检索弹性盒子元素在主轴(横轴)方向上的对齐方式
        * justify-content:flex-start 从主轴开始的方向对齐 (起点对齐)
        * justify-conten:flex-end;从主轴结束的方向对齐(终点对齐)
        * justify-content:center; 居中对齐
        * justify-content:space-around; 在父盒子中平分
        * justify-content:space-between; 两端对齐 平分
    + align-items调整侧轴(纵轴)对齐
        * align-items设置或检索弹性盒子元素在主轴（纵轴）方向上的对齐方式。
        * align-items:flex-start  从侧轴开始的放行对齐(起点对齐)
        * align-items:flex-end;从侧轴结束额方向对齐(终点对齐)
        * align-items:center; 居中
        * align-items:baseline; 基线对齐 默认同flex-start
        * align-items:stretch; 拉伸
    + flex子项目在主轴的缩放比例，不指定flex属性，则不参与伸缩分配
    + 以下属性了解
    + flex-wrap控制是否换行
    + align-content堆栈（由flex-wrap产生的独立行）对齐
    + flex-flow是flex-direction、flex-wrap的简写形式
    + order控制子项目的排列顺序，正序方式排序，从小到大

### 1.2 多列布局
- 将文档分成3列
-webkit-column-count: 3;
- 设置分栏间距
-webkit-column-gap: 50px;
- 设置分割线的颜色
-webkit-column-rule: 1px dashed red;
- 设置分栏的宽度
-webkit-column-width:200px;

## 2. Web字体
### 2.1 定义阐述
开发人员可以为自已的网页指定特殊的字体，无需考虑用户电脑上是否安装了此特殊字体，从此把特殊字体处理成图片的时代便成为了过去。
支持程度比较好，甚至IE低版本浏览器也能支持。

- 使用步骤：
    1. 引入字体包
    2. 申明字体：告诉浏览器去哪找字体
    3. 定义类名
    4. 在结构中写 图标的编码，给标签添加类名

### 2.2	字体格式
不同浏览器所支持的字体格式是不一样的，我们有必要了解一下有关字体格式的知识。

1. TureTpe(.ttf)格式
.ttf字体是Windows和Mac的最常见的字体，是一种RAW格式，支持这种字体的浏览器有IE9+、Firefox3.5+、Chrome4+、Safari3+、Opera10+、iOS Mobile、Safari4.2+；
2. OpenType(.otf)格式
.otf字体被认为是一种原始的字体格式，其内置在TureType的基础上，支持这种字体的浏览器有Firefox3.5+、Chrome4.0+、Safari3.1+、Opera10.0+、iOS Mobile、Safari4.2+；
3. Web Open Font Format(.woff)格式
woff字体是Web字体中最佳格式，他是一个开放的TrueType/OpenType的压缩版本，同时也支持元数据包的分离，支持这种字体的浏览器有IE9+、Firefox3.5+、Chrome6+、Safari3.6+、Opera11.1+；
4. Embedded Open Type(.eot)格式
.eot字体是IE专用字体，可以从TrueType创建此格式字体，支持这种字体的浏览器有IE4+；
5. SVG(.svg)格式
.svg字体是基于SVG字体渲染的一种格式，支持这种字体的浏览器有Chrome4+、Safari3.1+、Opera10.0+、iOS Mobile Safari3.2+；
了解了上面的知识后，我们就需要为不同的浏览器准备不同格式的字体，通常我们会通过字体生成工具帮我们生成各种格式的字体，因此无需过于在意字体格式间的区别差异。 
下载字体的网站.
推荐http://www.zhaozi.cn/、http://www.youziku.com/ 查找更多中文字体
6. 使用方法
```
 @font-face {font-family: 'webfont';
    src: url('font/webfont.eot'); /* IE9*/
    src: url('font/webfont.eot?#iefix') format('embedded-opentype'), /* IE6-IE8 */
    url('font/webfont.woff') format('woff'), /* chrome、firefox */
    url('font/webfont.ttf') format('truetype'), /* chrome、firefox、opera、Safari, Android, iOS 4.2+*/
    url('font/webfont.svg#webfont') format('svg'); /* iOS 4.1- */
}
/* 定义一个类名，谁加这类名，就会使用webfont字体*/
.webfont{
    font-family: 'webfont';
}
```

### 2.3	字体图标
其实我们可以把文字理解成是一种特殊形状的图片，也可以把图片制作成字
常见的是把网页常用的一些小的图标，借助工具帮我们生成一个字体包，然后就可以像使用文字一样使用图标了。
- 优点：
    + 将所有图标打包成字体库，减少请求；
    + 具有矢量性，可保证清晰度；
    + 使用灵活，便于维护；
- Font Awesome 使用介绍
    http://fontawesome.dashgame.com/
- 定制自已的字体图标库
    + http://iconfont.cn/
    + https://icomoon.io/
- SVG素材  http://www.iconsvg.com/
- 使用方法
```
@font-face {font-family: 'my-icon';
    src: url('font/iconfont.eot'); /* IE9*/
    src: url('font/iconfont.eot?#iefix') format('embedded-opentype'), /* IE6-IE8 */
    url('font/iconfont.woff') format('woff'), /* chrome、firefox */
    url('font/iconfont.ttf') format('truetype'), /* chrome、firefox、opera、Safari, Android, iOS 4.2+*/
    url('font/iconfont.svg#iconfont') format('svg'); /* iOS 4.1- */
}
.my-font{
font-family: "my-icon";
}
```

## 3. 鼠标滚动事件
```
  var num=0;
//    鼠标滚轮事件
    window.onmousewheel=function(){
        num++;
        console.log(num);
    }
```

    