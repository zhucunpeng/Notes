# **三大家族__client家族**
## 1.1 主要成员
1. clientWidth	获取网页可视区域宽度（两种用法）
clientHeight  获取网页可视区域高度（两种用法）
    + 调用者不同，意义不同：
    + 盒子调用：指盒子本身。
    + body/html调用：可视区域大小。	
2. clientX  鼠标距离可视区域左侧距离（event调用）
clientY 鼠标距离可视区域上侧距离（event调用）
3. clientTop/clientLeft 盒子的border宽高

## 1.2	三大家族区别（三大家族总结）
- Width和height
    + clientWidth  = width  + padding
    + clientHeight  = height + padding
    + offsetWidth  = width  + padding + border
    + offsetHeight  = height + padding + border
    + scrollWidth   = 内容宽度（不包含border）
    + scrollHeight  = 内容高度（不包含border）
    IE567高度可以比盒子小。IE8+火狐谷歌不能比盒子小
- top和left
    + offsetTop/offsetLeft ：
        * 调用者：任意元素。(盒子为主)
        * 嘛作用：距离父系盒子中带有定位的距离。
    + scrollTop/scrollLeft:(盒子也可以调用，必须有滚动条)
        * 调用者：document.body.scrollTop/.....(window)
        * 嘛作用：浏览器无法显示的部分（被卷去的部分）。
    + clientY/clientX:（clientTop/clientLeft 值的是border）
        * 调用者：event.clientX(event)
        * 嘛作用：鼠标距离浏览器可视区域的距离（左、上）。

## 1.3 client家族之:检浏览器宽/高度(可视区域)
- ie9及其以上的版本
window.innerWidth/Height  
- 标准模式（有DTD）（“CSS1Compat”）
document.documentElement.clientWidth
document.documentElement.clientHeight
- 怪异模式 （没有DTD）
document.body.clientWidth
document.body.clientHeight

## 1.4 事件总结
onresize 事件会在窗口或框架被调整大小时发生

- window.onscroll        	屏幕滑动
- window.onresize      	浏览器大小变化
- window.onload	         页面加载完毕
- div.onmousemove    		鼠标在盒子上移动
		（注意：不是盒子移动！！！）
- onmouseup/onmousedown  ==  onclick

## 1.5 获得屏幕宽高
> window.screen.width
分辨率是屏幕图像的精密度，指显示器所能显示的像素有多少。
我们的电脑一般：
横向1280个像素点，
纵向960个像素点。

        