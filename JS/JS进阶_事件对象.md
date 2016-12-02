# **事件对象(event)**
## 1.1定义阐述
> 所有的浏览器都支持event对象，但支持的方式不同
普通浏览器支持 event（带参，任意参数）
ie 678 支持 window.event（无参，内置）
总结：他是一个事件中的内置对象。内部装了很多关于鼠标和事件本身的信息。

## 1.2 事件对象的捕获(event的获取)
- IE678中，window.event 
- 在火狐谷歌中，event或者，在事件绑定的函数中，加参，这个参数就是event.
    + Box.onclick = function (aaa){   aaa就是event     }

## 1.3 兼容获取方式有两种：
- 不写参数直接使用event;
- 写参数，但是为event....var event  = event || window.event;(主要用这种)

## 1.4 event属性
- pageX    光标相对于该网页的水平位置（ie无）
- pageY    光标相对于该网页的垂直位置（ie无）
- screenX  光标相对于该屏幕的水平位置
- screenY  光标相对于该屏幕的垂直位置
- clientX  光标相对于该网页的水平位置 （当前可见区域）
- clientY  光标相对于该网页的垂直位置
- bubbles  返回布尔值，指示事件是否是起泡事件类型。
- button   返回当事件被触发时，哪个鼠标按钮被点击。
- timeStamp 返回事件生成的日期和时间。
- target   该事件被传送到的对象
- type     事件的类型

## 1.5 creenX、pageX和clientX的区别
- PageY/pageX: 鼠标位于整个网页页面的顶部和左侧部分的距离。（页面）
- ScreenY/screenX: 鼠标位于屏幕的上方和左侧的距离。（屏幕）
- ClientX/clientY: 鼠标位于浏览器的左侧和顶部的距离。（浏览器大小和位置）
- ![](leanote://file/getImage?fileId=584101fb334ed27670000000)

## 1.6 PageY和pageX的兼容写法（很重要）
> 
在页面位置就等于 = 看得见的+看不见的
pageY/pageX=event.clientY/clientX+scroll().top/scroll().left

## 1.7 鼠标拖拽效果  常用事件
- onmouseover  鼠标经过
- onmouseenter 
- onmouseleave
- onmouseout  鼠标离开
- onmousedown  鼠标按下
- onmouseup  鼠标弹起
- onmousemove  鼠标移动（1px也触动
- 注意：
> onmouseover、onmouseout事件给定一个盒子，子元素也会获取这个事件。替代方法：onmosueenter和onmouseleave.

## 1.8 清除选中的内容
- IE9、Firefox、Safari、Chrome和Opera支持：window.getSelection() 
- IE9以下支持：document.selection 
- 兼容写法：
> window.getSelection?window.getSelection().removeAllRanges():document.selection.empty();

## 1.9 模拟垂直滚动条口诀
- 动态设置滚动条的高度 scrollBarHeight = 
（ 容器的高度 / 内容的高度*容器的高度 ）
- 滚动条滚动一次    内容移动的距离
(内容的高度 - 容器的高度)   / (容器的高度 - 滚动条的高度)* 滚动条移动的距离


