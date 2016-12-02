# **1. 动画和封装**
## 1.1 动画的分类
- 闪现   
    div.style.left ="500px"
- 匀速
- 缓动

## 1.2 动画原理
**盒子未来的位置 = 盒子现在的位置 + 步长；**
> 
style.left赋值，用offsetLeft获取值。
style.left获取值不方便，获取行内式，如果没有值“”；容易出现NaN；
offsetLeft获取值特别方便，而且是现成number方便计算。因为他是只读的不能赋值。

## 1.3 缓动动画原理
**动画原理 = 盒子位置 + 步长（步长越来越小）**
> 
leader=leader+(target-leader)/10;
    盒子位置 = 盒子本身位置+（目标位置-盒子本身位置）/ 10；


## 1.4 动画封装实例代码
```
 var btnArr = document.getElementsByTagName("button");
    var box = document.getElementsByClassName("box")[0];
    //绑定事件
    btnArr[0].onclick = function () {
        //如果有一天我们要传递另外一个盒子，那么我们的方法就不好用了
        //所以我们要增加第二个参数，被移动的盒子本身。
        animate(box,200);
    }
 
    function animate(ele,target){
        //要用定时器，先清除定时器
        //一个盒子只能有一个定时器，这样儿的话，不会和其他盒子出现定时器冲突
        //而定时器本身就成为盒子的一个属性
        clearInterval(ele.timer);
        //我们要求盒子既能向前又能向后，那么我们的步长就得有正有负
        //目标值如果大于当前值取正，目标值如果小于当前值取负
        var speed = target>ele.offsetLeft?10:-10;
        ele.timer = setInterval(function () {
            //在执行之前就获取当前值和目标值之差
            var val = target - ele.offsetLeft;
            ele.style.left = ele.offsetLeft + speed + "px";
            //目标值和当前值之差如果小于步长，那么就不能在前进了
            //因为步长有正有负，所有转换成绝对值来比较
            if(Math.abs(val)<Math.abs(speed)){
                ele.style.left = target + "px";
                clearInterval(ele.timer);
            }
        },30)
    }

```

## 1.5 缓动动画封装实例代码
```
 var　btn = document.getElementsByTagName("button")[0];
    var　div = document.getElementsByTagName("div")[0];

    var timer = null;

    btn.onclick = function () {
        //要用定时器，先清定时器
        clearInterval(timer);
        timer = setInterval(function () {
            var target = 0;
            //缓动。如何缓动呢？步长越来越小....
            //   步长用目标位置和盒子自身位置的十分之一
            //最后10像素的时候都是1像素1像素的向目标位置移动，就能够到达指定位置。
            var step = (target - div.offsetLeft)/10;
            //每次获取步长都向上取整，这种情况就包含step<0.4的情况
            //拓展：差值大于0的时候，向上取整，小于0的时候向下取整。
            //step = Math.ceil(step);
            step = step>0?Math.ceil(step):Math.floor(step);
            //step = target>div.offsetLeft?Math.ceil(step):Math.floor(step);

            //动画原理：盒子未来的位置 = 盒子当前的位置+步长
            div.style.left = div.offsetLeft + step + "px";
            //跳出条件：目标位置-当前位置的绝对值，小于步长
            console.log(1);
            if(Math.abs(0-div.offsetLeft)<Math.abs(step)){
                div.style.left = 0+"px";
                clearInterval(timer);
            }
        },30);
    }
```

## 1.6 缓动动画框架封装(回调函数)实例代码
```
 <body>
 <button>运动到400然后回来</button>
 <div></div>
 <script>
     var btnArr=document.getElementsByTagName("button");
     var div = document.getElementsByTagName("div")[0];
 
     btnArr[0].onclick = function(){
         var json1={"left":300,"top":200.5,"width":300,"height":200};
         var json2={"left":10,"top":30,"width":100,"height":100};
         animate(div,json1,function(){
             animate(div,json2)
         });
     }
 
     //参数为三个变量
     function animate(ele,json,fn){
         //先清除定时器
         clearInterval(ele.timer);
         ele.timer = setInterval(function(){
             //开闭原则
             var bool = true;
 
             //遍历属性和值 分别单独处理json
             //attr==k(键)  target == json[k] (值)
             for(var k in json){
                 var leader = parseInt(getStyle(ele,k)) || 0 ;
                 var step = (json[k]-leader)/10;
                 step = step>0?Math.ceil(step):Math.floor(step);
                 ele.style[k]= leader+ step +"px";
                 if(Math.abs(json[k]-leader)>Math.abs(step)){
                     bool=false;
                 }
 
                 //清除定时器
                 //判断 目标值和当前值的差大于步长 就不能跳出循环
                 //不考虑小数的情况 目标位置和当前位置不想等 就不能清除定时器
                 if(json[k] !== leader){
                     bool = false;
                 }
             }
             //只有所有的属性都到了指定位置，bool值才会变成false
             if(bool){
                 for(var j in json){
                     ele.style[j]=json[j]+"px";
                 }
                 clearInterval(ele.timer);
                 //所有程序执行完毕了 现在可以执行回调函数了
                 //只有传递了回调函数 才能执行
                 if(fn){
                     fn();
                 }
             }
         },30);
     }
 
     //兼容方法获取元素样式
     function getStyle(ele,attr){
         if(window.getComputedStyle){
             return getComputedStyle(ele,null)[attr];
         }
         return ele.currentStyle[attr];
     }
 
 </script>
 </body>
```


## 1.7 缓动动画框架封装(透明度&层级)
```
<body>
    <button>运动到400然后回来</button>
    <div></div>
    <script>
    var btnArr = document.getElementsByTagName("button");
    var div = document.getElementsByTagName("div")[0];

    btnArr[0].onclick = function() {
        var json1 = {
            "left": 300.4,
            "top": 200,
            "width": 300.6,
            "height": 200,
            "border-radius": 100,
            "opacity": 30,
            "zIndex": 2
        };
        animate(div, json1);

    }

    //参数变为3个
    function animate(ele, json, fn) {
        //先请定时器
        clearInterval(ele.timer);
        ele.timer = setInterval(function() {
            //开闭原则
            var bool = true;

            //遍历属性和值 分别单独处理json
            //attr == k 键 target==json[k] 值
            for (var k in json) {
                var leader;
                //判断如果属性为opacity的时候 特殊获取值
                if (k === "opacity") {
                    leader = getStyle(ele, k) * 100 || 0;
                } else {
                    leader = parseInt(getStyle(ele, k)) || 0;
                }


                var step = (json[k] - leader) / 10;
                step = step > 0 ? Math.ceil(step) : Math.floor(step);
                leader = leader + step;

                //赋值 特殊情况 特殊赋值
                if (k === "opacity") {
                    ele.style[k] = leader / 100;
                    //兼容IE678
                    ele.style.filter = "alpha(opacity=" + leader + ")"
                } else if (k === "zIndex") {
                    ele.style.zIndex = json[k];
                } else {
                    ele.style[k] = leader + "px";
                }



                //清除定时器
                //判断 目标值和当前值的差大于步长 就不能跳出循环
                //不考虑小数的情况 目标位置和当前位置不想等 就不能清除定时器
                // if(json[k] !== leader){
                //   bool = false;
                // }
                if (Math.abs(json[k] - leader) > Math.abs(step)) {
                    bool = false;
                }
            }
            console.log(1);
            if (bool) {
                for (var j in json) {
                    ele.style[j] = json[j] + "px";
                }
                clearInterval(ele.timer);
                if (fn) {
                    fn();
                }
            }
        }, 30);

        function getStyle(ele, attr) {
            if (window.getComputedStyle) {
                return window.getComputedStyle(ele, null)[attr];
            }
            return ele.currentStyle[attr];
        }
    }
    </script>
</body>

```