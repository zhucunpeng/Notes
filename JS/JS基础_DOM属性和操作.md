#DOM操作
##1. 事件
###1.1 概述
JS是以事件驱动为核心的一门语言
###1.2 事件三要素
>事件源、事件、事件驱动程序

* a、获取事件源
    获取事件源一共5种
document.getElementById("box");
document.getElementsByTagName("div");
document.getElementsByClassName("leiming");
要求掌握上面三种，下面不掌握
document.getElementsByName("aaa");
* b、绑定事件
box.onclick = function(){ 程序 };
* c、书写事件驱动程序
以后要学习的关于DOM的操作

###1.3 事件有哪些
* a、onclick  鼠标单击
* b、ondblclick 鼠标双击
* c、onkeyup            按下并释放或下拉菜单中的选项发生改变
* d、onchange         文本内容或下拉菜单中的选项发生改变
* e、onfocus             获取焦点，表示文本框等获得鼠标光标
* f、onblur                失去焦点，表示文本框等失去鼠标光标
* g、onmouseover    鼠标悬停，即鼠标停留在图片等的上方
* h、onmouseout      鼠标移出，即离开图片等所在区域
* i、onload                网页文档加载事件
* j、onunload            关闭网页时
* k、onsubmit           表单提交事件
* l、onreset               重置表单

###1.4 onload事件
>什么条件下触动这个事件呢？页面加载（文本和图片）完毕的时候。?
用途
js的加载时和html同步加载的。（如果使用元素在定义元素之间，容易报错。）
整个页面上所有元素加载完毕在执行js内容
window.onload可以预防使用标签在定义标签之前。
 
##2. DOM概述
###2.1 解析过程?
>HTML加载完毕，渲染引擎会在内存中巴HTML文档，生成一个DOM树，getElementById是和获取内种DOM上的元申诉节点，然后操作的时候改的是该元素的属性

###2.2 DOM(文档对象模型)
* a、document是文档对象模型的一部分
* b、DOM是一个符合的数据类型
>DOM就是把HTML视为一个层次结构(树形结构)的文档

 * 文档(Document)：就是指HTML或者XML文件
 * 节点(Node)：HTML文档中的所有内容都可以称之为节点
 * 元素(Element)：HTML文档中的标签可以称为元素 
 
###2.3 DOM节点的获取
操作节点,必须首先找到该元素,有三种方法来做这件事:

* a、通过id找到HTML元素
document.getElementById("demo");
* b、通过标签名找到HTML元素
document.getElementsTagName("div");
* c、通过类名找到HTML元素
document.getElementByClassname("a");
* d、通过类名查找 HTML 元素在 IE 5,6,7,8 中无效
标签=document.getElementById("demo"); 通过ID获得标签
他的返回值是一个标签，可以直接使用。获得属性值，设置属性。
标签数组= document.getElementsByTagName("div"); 通过标签名获得标签数组
标签数组= document.getElementsByClassName("a");通过类名获得标签数组
他们两个的返回值是标签数组，习惯性是遍历之后再使用。
特殊情况：数组中的值只有1个。     
document.getElementsByTagName("div")[0];取数组中第一个元素
document.getElementsByClassName("a")[0];取数组中第一个元素

##3. DOM访问关系(节点的获得)
节点的访问关系，是以属性的方式存在的，DOM的节点并不是孤立的，因此可以通过DOM节点之间的相对关系对他们进行访问
###3.1 父节点（parentNode）
* a、调用方式就是 节点.parentNode
调用者就是节点,一个节点只有一个父节点
* b、案例代码
```javascript
var box2 = document.getElementById("box2")
console.log(box2.parentNode);
```

###3.2 兄弟节点
>sibling:就是兄弟的意思
next:下一个的意思
previous:前一个的意思

* a、下一个兄弟节点=节点.nextElementSibling || 节点.nextSibling
 * ①.nextSibling: 调用者是节点在IE678中指下一个元素节点(标签),在火狐谷歌IE9+以后都指的是下一个节点(包括空文档和换行节点).
 * ②. nextElementSibling:在火狐谷歌IE9都指的是下一个元素节点
总结:在IE678中用nextSibing,在火狐谷歌IE9+以后用nextElementSibing
* b、前一个兄弟节点=节点.previousElemnentSibling || 节点.previousSibling
 * ①. previousSibling:调用者是节点,IE678中指前一个元素节点(标签).在火狐谷歌IE9+以后都指的是前一个节点(包括空文档和换行节点)
 * ②. previousSibling:在火狐谷歌IE9都指的是下一个元素节点
总结:在IE678中用previousSibling,在火狐谷歌IE9+以后用previousElementSibling
 
###3.3 单个子节点
* a、第一个子节点=父节点.firstElementChild || 父节点.firstChild
 * ①.first:调用者是父节点,IE678中指第一个子元素节点(标签).在火狐谷歌IE9+以后都指的是第一个节点(包括文档和换行节点)
 * ②. firstElementChild:在火狐谷歌IE9都指的第一个元素节点
* b、最后一个兄弟节点=父节点.lastElementChild ||父节点.lastChild
 * ①. lastChild:调用者是父节点,IE678中指最后一个子元素节点(标签),在火狐谷歌IE9+以后都指的是最后一个节点(保罗空文档和换行节点)
 * ②. lastElementChild:在火狐谷歌IE9+都指的是最后一个元素节点
 
###3.4 所有子节点
* a、子节点数组=父节点.childNodes  获取所有节点
ChildNodes:它是标准属性,他返回指定元素的子元素集合,包括HTML节点 所有属性 文本节点 (它是W3C的亲儿子)
火狐 谷歌等高版本会把换行也看做是子节点
 * ①.nodeType = 1  表示的是元素节点  记住 元素就是标签
 * ②. nodeType = 2 表示属性节点
 * ③. nodeType = 3  表示文本节点
* b、子节点数组=父节点.children;  用的最多
children:非标准属性,他返回指定元素的子元素集合,
但他只返回HTML节点,甚至不反悔文本节点,虽然不是标准的DOM属性,但他和innerHTML方法一样,得到了几乎所有浏览器的支持,
children 在IE678中包含注释节点,
在IETF78中,注释节点不要写在里面

###3.5 知识补充
* a、节点自己.parentNode.children[index]; 随意得到兄弟节点
* b、获取所有的兄弟节点

```
function siblings(elm){
var a=[ ];
var p=elm.parentNode.children;
for(var i=0;i<p.length;i++){
if(p[i] !==elem){
a.push(p[i]);
}
}
return  a;
}
``` 
##4. DOM节点操作
###4.1 创建节点
新的标签(节点)=document.creatElement("标签名");
###4.2 插入节点(使用节点)
* a、父节点.appendChild( );
父节点.appendChild(新节点); 父节点的最后插入一个新节点
* b、父节点.insertBefore(要插入的节点,参考节点)
父节点.insertBefore(新节点,参考节点) 在参考节点前插入
如果参考节点为null,那么他将在节点最后插入一个节点

###4.3 删除节点
* a、用法:用父节点删除子节点
父节点.removeChild(子节点); 必须指定要删除 的子节点
节点自己删除自己;
不知道父级的情况下,可以这么些:node.parentNode.removeChild(node)

###4.4 复制节点
* a、oldNode.cloneNode(true)
新节点=要复制的节点.cloneNode(参数); 参数可选复制节点
用于复制节点,接收一个布尔参数,true表示深复制(赋值节点及其所有子节点),false表示浅复制(复制节点本身,不复制子节点)

###4.5 属性、赋值获取两种方式
* a、元素节点.属性或者元素节点[属性]
```
eleNode.src="image/jd2.png"
console.log(eleNode.src);
console.log(eleNode["title"]);
```
* b、元素节点.方法( );
 * ①.获取: getAttribute(名称)  属性节点
 * ②.设置:setAttribute(名称,值)
 * ③.删除:removeAttribute(名称)
调用者:节点   有参数 没有返回值 每一个方法意义不同
```
示例代码:
<body>
<div id="box" value="111">你好</div>
<script>
var ele = document.getElementById("box");//元素节点
var att = ele.getAttributeNode("id");//属性节点
var txt = ele.firstChild;
console.log(ele);  //<div id="box" value="111">你好</div>
console.log(att); //id="box"
console.log(txt); //"你好"
```

###4.6 节点属性
>value和innerHTML和innerText和textContent

* a、value:标签的value属性
* b、innerHTML:获取双闭合标签里面的内容(识别标签)
* c、innerText:获取双闭合标签里面的内容(不识别标签)(老版本的火狐用textContent)
    * ①.老版本的火狐不支持innerText，支持textContent
    * ②.p不能嵌套p。h1不能嵌套h1。a连接内部不能嵌套a连接
 
##5. style属性演示
>var box = document.getElementsByTagName("div")[0];

- 5.1 样式少的时候使用,
```
console.log(box.style.backgroundColor);
```
- 5.2 style是对象
```
console.log(box.style);
console.log(typeof box.style);
```
- 5.3 值是字符串，没有设置值是“”；
```
console.log(box.style.lineHeight);
console.log(box.style.border);
```
- 5.4 命名规则，驼峰命名。和css不一样
```
console.log(box.style.backgroundColor);
```
- 5.5 设置了类样式不能获取。（只和行内式交互，和内嵌和外链无关）
```
console.log(typeof box.className);
```
- 5.6 box.style.cssText = “字符串形式的样式”；
```
console.log(box.style.cssText);
box.style.cssText = "width: 200px; height: 200px; background-color: red;line-height:200px;text-align:center;" 
```

##6. 定时器
###6.1 两种定时器
* a、setInterval( )
循环定时器:周而复始的执行(循环执行),比较常用
* b、setTimeout( )
炸弹定时器:用完以后立刻报废(只执行一次)

##6.2 setInterval( )定义的方法
* a、方式一(匿名函数)
```
setInterval(function () {
console.log(1);
},1000);
```

* b、方式二
```
setInterval(fn,1000);
function fn(){
console.log(2);
}
```
* c、方式三
```
setInterval("fn(3)",1000);
function fn(aaa){
console.log(aaa);
}
```

##6.3 清除定时器
```
//返回值，清除定时器。
var num = 1;
//setInterval他的返回值就是定时器的名字
var timer = setInterval(function () {
console.log(num);
num++
if(num===10){
//如何停止定时器呢？？？
clearInterval(timer);
}
},500);
```

##**7、内置对象String/Number/Boolean**
###**7.1、给索引查字符(charAt/charCodeAt)**
###7.1.1、字符/字符编码 = Str.charAt/charCodeAt(索引值);
>①charAt，获取相应位置字符（参数： 字符位置）
>>注释：字符串中第一个字符的下标是 0。如果参数 index 不在 0 与 string.length 之间，该方法将返回一个空字符串。

>②charCodeAt获取相应位置字符编码（参数： 字符位置）。

###7.1.2、charAt()方法和charCodeAt()方法用于选取字符串中某一位置上的单个字符
>###区别：charCodeAt()方法，它并不返回指定位置上的字符本身，而是返回该字符在Unicode字符集中的编码值。如果该位置没有字符，返回值为NaN.

###**7.2、给字符查索引（indexOf/lastIndexOf）**
###7.2.1、索引值 = str.indexOf/lastIndexOf(想要查询的字符);
>①indexOf，从前向后索引字符串位置（参数： 索引字符串）
>>从前面寻找第一个符合元素的位置

>②lastIndexOf，从后向前索引字符串位置（参数：索引字符串）
>>从后面寻找第一个符合元素的位置
找不到则返回 -1

###**7.3、url 编码和解码（了解）**
###7.3.1、encodeURIComponent() 函数可把字符串作为 URI 组件进行编码
###7.3.2、decodeURIComponent() 函数可把字符串作为 URI 组件进行解码
>URI (Uniform ResourceIdentifiers,通用资源标识符)进行编码，以便发送给浏览器。有效的URI中不能包含某些字符，例如空格。而这URI编码方法就可以对URI进行编码，它们用特殊的UTF-8编码替换所有无效的字符，从而让浏览器能够接受和理解。

###**7.4、字符串的链接**
>新字符串 = str1.concat(str2);链接两个字符串

###**7.5、字符串的截取**
###7.5.1、slice，截取字符串（参数：1，截取位置【必须】，2终结点）
字符串 = str.slice（索引1，索引2); 两个参数都是索引值。

* （2,5）  正常包左不包右。
*  ( 2 )   	从指定的索引位置剪到最后。
* （-3）   从倒数第几个剪到最后.
* （5,2）  前面的大，后面的小，空。

###7.5.2、 substr，截取字符串（参数：1，截取位置【必须】，2截取长度）
字符串 = str.substr（参数1，参数2); 1索引值,2长度。
第一个参数为从索引位置取值，第二个参数返回字符长度。

* （2,4）    从索引值为2的字符开始，截取4个字符。
* （1）     一个值，从指定位置到最后。
* （-3）    从倒数第几个剪到最后.
*  不包括前大后小的情况。

###7.5.3、 slice，截取字符串（参数：1，截取位置【必须】，2终结点）
字符串 = str.slice（索引1，索引2); 两个参数都是索引值。
不同1：参数智能调转位置。
不同2：参数负值，将全部获取字符串。

* (2,5)    正常包左不包右。
* ( 2 )      从指定的索引位置剪到最后。
* (-3)    获取全部字符串.
* (5,2)   前面的大，后面的小，不是空。（2,5）

###**7.6、特殊方法简介**
* trim()     //只能去除字符串前后的空白
* replace()  //替换   str.replace(/aaa/gi,“bbb”);g 通用的意思 str里面的全部替换  //i 不区分大小写
* split()    //字符串变数组
* 大小写转换方法
    * ①str.toLowerCase()  //转换大写
    * ②str.toUpperCase() //转换小写

##**8、Math**
* Math.abs();       取绝对值
* Math.floor();      向下取整 向小取
* Math.ceil();       向上取整 向大取
* Math.round();     四舍五入取整 正数四舍五入 负数五舍六入
* Math.random();   随机数0-1

##**9、事件监听**
###**9.1、事件监听原理：**
```
//原理（了解）（自己封装一个）(click)
    function fn(str,fn,ele){
        //判断位置要注意：如果进入绑定事件本身，那么该事件已经本绑定了
        //所以获取旧的事件必须在新的事件绑定之前
        var oldEvent = ele["on"+str];
        ele["on"+str] = function () {
            //不能直接执行函数，因为我们还不知道以前有没有绑定我同样的事件
            //进行判断，如果以前有过绑定事件，那么把以前的执行完毕在执行现在的事件，如果没有就直接执行
            //如果没有被定义过事件该事件源的该事件属性应该是null对应的boolean值是false
            //如果已经定义过事件该事件源的该事件属性应该是function本身对应的boolean值是true
            if(oldEvent){
                //因为oldEvent本身他就是函数本身，那么后面加一个();就是执行函数
                oldEvent();
                fn();
            }else{
                //没有绑定过事件
                fn();
            }
        }
    }
```
###**9.2、事件添加的兼容：**
###9.2.1、火狐谷歌IE9+支持addEventListener
btn.addEventListener("click",fn1);
###9.2.2、IE678支持attachEvent
btn.attachEvent("onclick",fn1);
###9.2.3、事件添加兼容写法
```
 EventListen = {
        addEvent: function (ele,fn,str) {
            //通过判断调用的方式兼容IE678
            //判断浏览器是否支持该方法，如果支持那么调用，如果不支持换其他方法
            if(ele.addEventListener){
                //直接调用
                ele.addEventListener(str,fn);
            }else if(ele.attachEvent){
                ele.attachEvent("on"+str,fn);
            }else{
                //在addEventListener和attachEvent都不存在的情况下，用此代码
                ele["on"+str] = fn;
            }
        }
    }
```
###**9.3、事件移除的兼容：**
###9.3.1、火狐谷歌IE9+支持removeEventListener
btn.removeEventListener("click",fn1);
###9.3.2、IE678支持detachEvent
btn.detachEvent("onclick",fn1);
###9.3.3、事件移除兼容写法
```
removeEvent: function (ele,fn,str) {
            if(ele.removeEventListener){
                ele.removeEventListener(str,fn);
            }else if(ele.detachEvent){
                ele.detachEvent("on"+str,fn);
            }else{
                ele["on"+str] = null;
            }
        }
```
###**9.4、addEventListener和attachEvent的区别：**
###9.4.1 事件名称的区别
addEventLisener中第一个参数type是click、load，不带on
attachEvent中一个参数type是onclick、onload
###9.4.2 this的区别
addEventLisener：事件处理程序会在当前对象的作用域运行，因此，时间处理程序的this就是当前对象
attachEvent：事件处理程序是在全局作用域下运行因此this就是window












