
## 水果选择排序版本

```html
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
    <style>
        select {
            width: 150px;
            height: 200px;
            background-color: #7bff68;
        }
    </style>
</head>
<body>
<select size="10" name="aaa" id="sel1" multiple="multiple">
    <option value="0">1香蕉</option>
    <option value="1">2苹果</option>
    <option value="2">3大鸭梨</option>
    <option value="3">4草莓</option>
</select>

<input type="button" value=">>>"/>
<input type="button" value="<<<"/>
<input type="button" value=">"/>
<input type="button" value="<"/>

<select size="10" name="bbb" id="sel2" multiple="multiple">

</select>

</body>
</html>
```

## 原始版本

```javascript
<script>
    //需求：点击按钮把对应的选中项移动到另一侧。
    //技术点：如果移动单一的选项，那么看看哪个选项是有selected的。
    //如果移动所有的选项，那么直接把sel1中的所有选项放入sel2中。

    //步骤：
    //1.获取事件源和相关元素
    //2.绑定事件
    //3.书写事件驱动程序

    //步骤：
    //1.获取事件源和相关元素
    var sel1 = document.getElementById("sel1");
    var sel2 = document.getElementById("sel2");
    var inpArr = document.getElementsByTagName("input");

    //2.绑定事件(push和appendChild用法相似：但是一个是控制数组，一个是控制元素节点)
    inpArr[0].onclick = function(){
        var optArr = sel1.children;
        for(var i = 0;i<optArr.length;){
            sel2.appendChild(optArr[i]);
        }
    }
    //第二个按钮
    inpArr[1].onclick = function(){
        var optArr = sel2.children;
        for(var i = 0;i<optArr.length;){
            sel1.appendChild(optArr[i]);
        }
    }
    //第三个按钮
    inpArr[2].onclick = function(){
        var optArr = sel1.children;
        for(var i=optArr.length-1;i>=0;i--){
            if(optArr[i].selected == true){
                optArr[i].selected = false;
                sel2.appendChild(optArr[i]);
            }
        }
        //获取sel2中的元素放到数组中，排序再放进去
        var aaa = Array.from(sel2.children).sort(function(a,b){
            return a.value - b.value;
        });
        //删除所有子元素
        for(var i =0;i<sel2.children.length;i++){
            sel2.removeChild(sel2.children[i]);
        }
        //把排好序的数组添加到sel2中
        for (var i = 0; i < aaa.length; i++) {
            sel2.appendChild(aaa[i]);
        }
    }

    //第四个按钮
    inpArr[3].onclick = function(){
        var optArr = sel2.children;
        for(var i = optArr.length - 1;i>=0;i--){
            if(optArr[i].selected == true){
                optArr[i].selected = false;
                sel1.appendChild(optArr[i]);
            }
        }
        var bbb = Array.from(sel1.children).sort(function(a,b){
            return a.value - b.value;
        });
        //删除所有子元素
        for(var i = 0;i<sel1.children.length;i++){
            sel1.removeChild(sel1.children[i]);
        }
        //把排好序的数组添加到sel1中
        for(var i = 0;i<bbb.length;i++){
            sel1.appendChild(bbb[i]);
        }
    }
</script>
```

## 封装版本
```
<script>
    var sel1 = document.getElementById("sel1");
    var sel2 = document.getElementById("sel2");
    var inpArr = document.getElementsByTagName("input");
    //封装版水果选择
    inpArr[0].onclick = function(){
        fn1(sel1,sel2);
    }
    inpArr[1].onclick = function(){
        fn1(sel2,sel1);
    }
    inpArr[2].onclick = function(){
        fn2(sel1,sel2);
    }
    inpArr[3].onclick = function(){
        fn2(sel2,sel1);
    }

    //前两个按钮，选取全部的
    function fn1(ele1,ele2){
        var arr = ele1.children;
        for(var i = arr.length - 1;i>=0;i--){
            ele2.appendChild(arr[0]);
        }
    }

    //后两个按钮，选取并按顺序添加
    function fn2(ele1,ele2){
        var arr = ele1.children;
        for(var i = arr.length - 1;i>=0;i--){
            if(arr[i].selected == true){
                arr[i].selected = false;
                ele2.appendChild(arr[i]);
            }
        }
        //把元素转换成真数组 并排序
        var arr1 = Array.from(ele2.children).sort(function(a,b){
            return a.value - b.value;
        });
        //删除放进去的所有子元素
        for(var i =0 ;i<ele2.children.length;i++){
            ele2.removeChild(ele2.children[i]);
        }
        //把排好序的数组添加到ele2中
        for(var i = 0;i<arr1.length;i++){
            ele2.appendChild(arr1[i]);
        }
    }


</script>

```

