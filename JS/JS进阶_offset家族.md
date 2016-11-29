# **三大家族_offset家族**
## 1.1 三大家族和一个事件对象
- offset 家族
- scroll家族
- client家族
- event事件对象

## 1.2 Offset家族简介
> offsetWidth和offsetHight以及offsetLeft和offsetTop以及offsetParent共同组成了offset家族。

### 1.2.1 offsetWidth和offsetHight（检测盒子自身宽高+padding+border）
> 这两个属性，他们绑定在了所有的节点元素上。获取之后，只要调用这两个属性，我们就能够获取元素节点的宽和高。

- offset宽/高  =  盒子自身的宽/高 + padding +border；不包含margin
- offsetWidth = width+padding+border；
- offsetHeight = Height+padding+border

### 1.2.2 offsetLeft和offsetTop（检测距离父盒子有定位的左/上面的距离）
> 返回距离上级盒子（带有定位）左边的位置如果父级都没有定位则以body为准
offsetLeft 从父亲的padding 开始算,父亲的border 不算。
在父盒子有定位的情况下，offsetLeft == style.left(去掉px)

###1.2.3 offsetParent（检测父系盒子中带有定位的父盒子节点）
- 1、返回改对象的父级 （带有定位）
	>如果当前元素的父级元素没有进行CSS定位（position为absolute或relative，fixed），offsetParent为body。

- 2、如果当前元素的父级元素中有CSS定位	
    > （position为absolute或relative，fixed），offsetParent取最近的那个父级元素。

## 1.3 offsetLeft和style.left区别
> 
1. 最大区别在于offsetLeft可以返回没有定位盒子的距离左侧的位置。
    - 如果父系盒子中都没有定位，以body为准。
    - style.left只能获取行内式，如果没有返回“”;
2. offsetTop 返回的是数字，而style.top返回的是字符串，除了数字外还带有单位：px。
    - div.offsetLeft = 100;    div.style.left = "100px";
3. offsetTop 只读，而 style.top可读写。（只读是获取值，可写是赋值）
    - style.left和style.top可以赋值
    - offsetLeft和offsetTop只能获取值
4. 如果没有给 HTML 元素指定过 top 样式，则style.top返回的是空字符串。
    - style.left只能获取行内式，如果没有返回“”;

**style.left在=的左边和右边还不一样。（左边的时候是属性，右边的时候是值）**







