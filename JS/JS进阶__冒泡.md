#**冒泡机制（event）**
## 1.1 定义阐述
> 事件冒泡: 当一个元素上的事件被触发的时候，比如说鼠标点击了一个按钮，同样的事件将会在那个元素的所有祖先元素中被触发。这一过程被称为事件冒泡；这个事件从原始元素开始一直冒泡到DOM树的最上层。(BUG)
（本来应该一人做事一人当，结果，我做错了事情，你去告诉我妈）

- 什么是冒泡：子元素事件被触动，父盒子的同样的事件也会被触动。
- 取消冒泡就是取消这种机制。

## 1.2 事件传播阶段
> 事件传播的三个阶段是：捕获、冒泡和目标阶段

- 事件捕获阶段：事件从最上一级标签开始往下查找，直到捕获到事件目标(target)。
- 事件冒泡阶段：事件从事件目标(target)开始，往上冒泡直到页面的最上一级标签。

## 1.3 冒泡顺序
- IE 6.0: 
div -> body -> html -> document
- 其他浏览器: 
div -> body -> html -> document -> window
> 
不是所有的事件都能冒泡。以下事件不冒泡：blur、focus、load、unload、onmouseenter
onmouseleave

## 1.4 阻止冒泡
- w3c的方法是：（火狐、谷歌、IE11）
	event.stopPropagation()
- IE10以下则是使用：event.cancelBubble = true
- 兼容代码如下：

```
  var event = event || window.event;
 if(event && event.stopPropagation){
            event.stopPropagation();
  }else{
            event.cancelBubble = true;
  }
```

## 1.5 事件委托
```
//普通的事件绑定，没有办法为新创建的元素绑定事件。所以我们要使用冒泡的特性，事件委托！
    //事件委托
    ul.onclick = function (event) {
        //获取事件触动的时候传递过来的值
        event = event || window.event;
        var aaa = event.target?event.target:event.srcElement;
        //判断标签名，如果是li标签弹窗
        if(aaa.tagName === "LI"){
            alert("我是li");
        }
    }
```

## 1.6 隐藏模态框
- 判断当前对象
- IE678    event.srcElement（事件源）
- 火狐/谷歌等  event.target（事件源）
- 兼容写法获取元素ID：
```
var event = event || window.event;
var targetId =  event.target ?  event.target.id : event.srcElement.id;
```

## 1.7 变量属性获取/赋值方法
- 给属性赋值：（既能获取又能赋值）
    + div.style.width     单个赋值
    + div.style[“width”]  变量赋值

- 获取属性值：（只能获取）
    + div.currentStyle.width;   IE678 	单个获取
    + window.getComputedStyle(div,null).width;
    + div.currentStyle[“width”];   IE678		变量获取
    + window.getComputedStyle(div,null)[“width”];
参数1：获取属性的元素。
参数2：伪元素，C3学习。
- 兼容方法获取元素样式
```
        function getStyle(ele,attr){
            if(window.getComputedStyle){
                return window.getComputedStyle(ele,null)[attr];
            }
            return ele.currentStyle[attr];
        }
```

## 1.8 透明度
- opacity: 0.5;  内容一起透明.(火狐谷歌IE9+)
	取值范围：  0-1
- filter: alpha(opacity=50);     IE678(不研究)
         取值范围：  0-100
