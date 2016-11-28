# BOM简介
## 1. window对象
### 1.1 window是JavaScript的顶级对象

### 1.2 所有定义在全局作用域中的变量和函数都是window对象中的属性和方法

### 1.3 window对象下的属性和方法调用的时候可以省略window

## 2. BOM的内置方法和内置对象
### 2.1 新窗口=window.open(地址,是否开新窗口,新窗口的参数)

* window.open(url,target,param)
* url 要打开的地址
* target新窗口的位置 _blank _self _parent(父框架)
* param 新窗口的一些设置 返回值，新窗口的句柄

以下是一些参数：
> name：新窗口的名称，可以为空
featurse：属性控制字符串，在此控制窗口的各种属性，属性之间以逗号隔开。
fullscreen= { yes/no/1/0 } 是否全屏，默认no
channelmode= { yes/no/1/0 } 是否显示频道栏，默认no
toolbar= { yes/no/1/0 } 是否显示工具条，默认no
location= { yes/no/1/0 } 是否显示地址栏，默认no
directories = { yes/no/1/0 } 是否显示转向按钮，默认no
status= { yes/no/1/0 } 是否显示窗口状态条，默认no
menubar= { yes/no/1/0 } 是否显示菜单，默认no
scrollbars= { yes/no/1/0 } 是否显示滚动条，默认yes
resizable= { yes/no/1/0 } 是否窗口可调整大小，默认no
width=number 窗口宽度（像素单位）
height=number 窗口高度（像素单位）
top=number 窗口离屏幕顶部距离（像素单位）
left=number 窗口离屏幕左边距离（像素单位）

### 2.2 关闭本页面
```
a2.onclick = function () {
window.close();
}
```

### 2.3 location对象
* a、location对象
window.location
location相当于浏览器地址栏可以将url解析成独立的片段
* b、location对象的属性

    * href
    * hash 返回url中#后面的内容，包含#
    * host 主机名，包括端口
    * hostname 主机名
    * pathname url中的路径部分
    * protocol 协议 一般是http、https
    * search 查询字符串
* c、location对象的方法

    * location.assign() 改变浏览器地址栏的地址，并记录到历史中
    * 设置location.href 就会调用assign()。一般使用location.href 进行页面之间的跳转
    * location.replace() 替换浏览器地址栏的地址，不会记录到历史中
    * location.reload()    重新加载
    
### 2.4 history对象

* a、后退
history.back()
history.go(-1) 0是刷新

* b、前进
history.forward()
history.go(1)