# **三大家族__scroll家族**
## 1 Scroll家族组成
### 1.1 ScrollWidth和scrollHeight（不包括border和margin）
> scrollWidth = width + padding;

- 检测盒子的宽高。（调用者：节点元素。属性。）
- 盒子内容的宽高。（如果有内容超出了，显示内容的高度;不超出是盒子本身高度）
- IE567高度可以比盒子小。 IE8+火狐谷歌不能比盒子小

### 1.2 scrollTop和scrollLeft
> 网页，被浏览器遮挡的头部和左边部分。被卷去的头部和左边部分。

- 他有兼容性问题
    +  未声明 DTD（谷歌只认识他）
    document.body.scrollTop
    + 已经声明DTD（IE678只认识他）
   document.documentElement.scrollTop
    + 火狐/谷歌/ie9+以上支持的
   window.pageYOffset
- 兼容写法
```
var aaa = window.pageYOffset || document.documentElement.scrollTop || document.body.scrollTop || 0;
```

## 1.3 获取title、body、head、html标签
- document.title --- 文档标题；
- document.head --- 文档的头标签
- document.body --- 文档的body标签；
- document.documentElement --- 这个很重要,它表示文档的html标签，也就是说，基本结构当中的html标签并不是通过document.html 去访问的，而是document.documentElement 。

## 1.5 scroll（）的封装
```
function scroll(){
            //如果这个属性存在，那么返回值应该是0-无穷大
            //如果没有返回值是undefined；
            //只要判断不是undefined就可以调用此方法
            //练习使用此种封装
            if(window.pageYOffset !== undefined){
//                var json = {
//                    "top": window.pageYOffset,
//                    "left": window.pageXOffset
//                };
//                return json;
                return {
                    "top": window.pageYOffset,
                    "left": window.pageXOffset
                };
            }else if(document.compatMode === "CSS1Compat"){
                return {
                    "top": document.documentElement.scrollTop,
                    "left": document.documentElement.scrollLeft
                };
            }else{
                return {
                    "top": document.body.scrollTop,
                    "left": document.body.scrollLeft
                };
            }

            简单封装（实际工作使用）
           return {
               "top": window.pageYOffset || document.body.scrollTop || document.documentElement.scrollTop,
               "left":  window.pageXOffset || document.body.scrollLeft || document.documentElement.scrollLeft
           }
        }

```

## 1.6判断页面有没有DTD
- document.compatMode === "BackCompat"
- BackCompat  未声明
- CSS1Compat  已经声明
IE678默认识别CSS1Compat ，无论有没有dtd
**注意大小写**
## 1.7 onscroll事件
只要页面滚动无论向左向右，向上向下，哪怕只有1px，都会触动这个事件
## 1.8 屏幕跳转
- window.scrollTo 
方法可把内容滚动到指定的坐标。
- 格式：scrollTo(xpos,ypos)
    + xpos	必需。要在窗口文档显示区左上角显示的文档的 x 坐标。
    + ypos	必需。要在窗口文档显示区左上角显示的文档的 y 坐标







