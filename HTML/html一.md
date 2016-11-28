# **Hyper text markup language**
>超文本标记语言。   超文本：超链接。（实现页面跳转）

## 1、认识网页
### 1.1 web 标准
W3c组织(万维网联盟)
html 结构标准 、css  表现标注、js 行为标准
### 1.2 浏览器内核
浏览器内核：也就是浏览器所采用的渲染引擎，渲染引擎决定了浏览器如何显示网页的内容 以及页面的格式信息 ===>浏览器兼容问题出现

* IE： Trident  ['traɪd(ə)nt]
* 谷歌欧鹏：blink  [blɪŋk]  谷歌之前和苹果共同开发webkit ,2013年谷歌和欧鹏共同开发blink
* 火狐：gecko  ['gekəʊ]
* 苹果： webkit
### 1.3 Url 地址
> 浏览器向服务器发送请求(通过http协议)
http协议:超文本传输协议，也就是浏览器和服务器端的网页传输数据的约束和规范

#### 协议规定格式：scheme://host.domain:port/path/filename
* scheme:定义因特网服务的类型，常见的就是http
* host: 定义域主机(http的默认主机是www)
* domain:定义因特网域名  比如:w3school.com.cn
* :post   定义端口号(网页默认端口:80)
* filename: 文件名称
## 2、标签
### 2.1 标签
#### 2.1.1 标签语义化：
> 好的语义化的网站标准就是去掉样式表文件之后，结构依然很清晰。

#### 2.1.2 标签语义化概念：
> 根据内容的结构化(内容语义化)，选择合适的标签(代码语义化)

### 2.1.3 标签语义化意义 
> 1. 网页结构合理
2. 有利于seo:和搜索引擎简历良好沟通，有了良好的结构和语义你的网页内容自然容易被搜索引擎抓取
3. 方便其他设备解析(如屏幕阅读器、盲人阅读器、移动设备)
4. 便于团队开发和维护
### 2.1.4 标签语义化注意事项
> 1. 尽可能少的使用无语义化的标签div和span
2. 在语义不明显时，既可以使用div或者p时，尽量用p, 因为p在默认情况下有上下间距，对兼容特殊终端有利；
3. 不要使用纯样式标签，如：b、font、u等，改用css设置。
4. 需要强调的文本，可以包含在strong或者em标签中strong默认样式是加粗（不要用b），em是斜体（不用i）

### 2.2 单标签
>* 注释标签   ctrl+/
* 换行标签   ```<br />```
* 水平线标签 ```<hr/>```
### 2.3 双标签
* ```<p>文本内容</p>```
> 特点：上下自动生成空白行。<br>换行不会生成空白行。

* ```<h1>标题标签</h1>```
> h1-h6  取值到h6，h1 在一个页面里只能出现一次。

* 文本标签  
> ```<font>文本内容</font>```

* 文本格式化标签
> 1.文本加粗标签```<strong></strong> <b></b>``` 工作里尽量使用strong
>2.文本倾斜标签```<em></em> <i></i>```     工作里尽量使用em
>3.删除线标签```<del></del> <s></s>```   工作里尽量使用del
>4.下划线标签```<ins></ins> <u></u>```    工作里尽量ins

* .图片标签  
    ```html
    <img src="志玲/悟空/swk.jpg" alt="" />
    Src    图片的来源   必写属性
    Alt    替换文本    图片不显示的时候显示的文字
    Title   提示文本    鼠标放到图片上显示的文字
    Width  图片宽度
    Height  图片高度
    图片没有定义宽高的时候，图片按照百分之百比例显示，如果只更改图片的宽度或者高度，图片等比例缩放
    ```

* .音乐标签 
    ```html
    <embed src="路径" hidden="true/no" 隐藏/显示
    <embed src=” 路径” ,
    属性设置:hidden=”true/no”面板显示=隐藏面板/显示面板,默认为no；
    autostart=”true/false” 自动播放=自动播放/不自动播放；         loop=”正整数/true/false” 循环次数/循环/不循环；
    starttime= mm:ss(分:秒) ；
    volume=0-100之间的整数 音量大小；
    height=控制面板的高度 width=#宽度 单位为像素；
    units=pixels/en指定高和宽的单位；
    controls=console默认值/smallconsole/playbutton/pausebutton/stopbutton/volumelever 一般正常面板/较小面板/只显示播放按钮/只显示暂停按钮/只显示停止按钮/只显示音量调节按钮；
    name=对象的名称；
    title=说明的文字；
    palette=color|color前景色|背景色；
    align=center/left/right/top/bottom/baseline/texttop/middle/absmiddle/absbottom 控制面板居中/居左/居右/顶部与当前行中的最高对象的顶部对齐/底部与基线对齐/底部与文本的基线对齐/顶部与当前行中的最高的文字顶部对齐/中间与当前行的基线对齐/中间与当前文本的中间对齐/底部与文字的额滴不对齐
    ```

* 7.滚动样式
    ```html
    <marquee behavior="" direction=""> </marquee>
    behaviour：设定滚动的方式  
    alternate:表示在两端之间来回滚动
    scroll:表示由一端滚到另一端  会重复
    side:表示由一端滚到另一端   不会重复
    direction:设置滚动的方向
    down/up/left/right:向下/上/左/右 滚动
    loop:设置滚动次数 -1一直滚下去
    ```

* 超链接标签 
```html
<a href="03图片标签.html" title="图片标签" target="_self">超链接</a>
href   去往的路径（跳转的页面） 必写属性
title    提示文本   鼠标放到链接上显示的文字
target=”_self”    默认值    在自身页面打开（关闭自身页面，打开链接页面） 
Target=”_blank”   打开新页面 （自身页面不关闭，打开一个新的链接页面）
```

* 锚链接   
>先定义一个锚点 ``` <p id="sd">```
>超链接到锚点 ```<a href="#sd">回到顶部</a>```

## 3、特殊字符
> 特殊字符 描述  字符的代码

* 空格符   &nbsp;
* < 小于号 &lt;
* > 大于号 &gt;
* & 和号  &amp;
* © 版权  &copy;
* ￥ 人民币 &yen;
* ® 注册商标    &reg;
* ℃ 摄氏度 &deg;
* ± 正负号 &plusmn;
* × 乘号  &times;
* ÷ 除号  &divide;
* 2 平方2(上标2)    &sup2;
* 3 平方3(上标3)    &sup3;

## 4、列表
### 4.1、无序列表
```html
<ul type="circle">
    <li></li>    列表项
</ul>
type=”square”      小方块
Type=”disc”       实心小圆圈
Type=”circle”      空心小圆圈
```

### 4.2、无序列表
```html
<ol type="1" start="2">
    <li></li>   列表项
</ol>
type="1,a,A,i,I” type的值可以为1,a,A,i,I
start="2” 必须为数字， 决定了开始的位置。
```

### 4.3、自定义列表
```
<dl>
    <dt></dt>   小标题
    <dd></dd>   解释标题
    <dd></dd>   解释标题
</dl>
```
 
 
 
 
 