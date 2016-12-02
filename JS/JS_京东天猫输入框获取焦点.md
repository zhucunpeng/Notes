#京东天猫输入框获取焦点
```
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
    <style>
        input {
            width: 300px;
            height: 36px;
            padding-left: 5px;
            color: #ccc;
        }
        label {
            position: absolute;
            top: 82px;
            left: 56px;
            font-size: 12px;
            color: #ccc;
            cursor: text;
        }
        .hide {
            display: none;
        }
        .show {
            display: block;
        }
    </style>
</head>
<body>
    京东:<input id="inp1" type="text" value="我是京东"/><br><br>
    淘宝:<label for="inp2">我是淘宝</label><input id="inp2" type="text"/><br><br>
    placeholder:<input type="text" placeholder="我是placeholder"/>

    <script>
        //需求:京东的获取焦点
        //思路:京东的input按钮获取了插入条光标立刻删除内容,失去插入条光标显示文字
        //步骤
        //1 获取事件源和相关元素
        //2 绑定事件
        //3 书写事件驱动程序
        
        //1 获取事件源和相关元素
        var inp1 =document.getElementById("inp1");
        //绑定事件(获取焦点事件)
        inp1.onfocus=function( ){
            //判断,如果input里面的内容是"我是京东",那么把值赋值为""
            if(this.value==="我是京东"){
                inp1.value="";
                }
            }
        //失去焦点事件
        inp1.onblur=function(){
            //失去焦点后判断,如果input内容为空,那么把内容赋值为我是京东
            if(this.value===""){
                inp1.value="我是京东";
            }
        }
        
        //需求:淘宝的获取焦点
        //思路:在input中输入文字,label标签隐藏,里面的文字变成空字符串,label显示
        //步骤
        //1 获取事件源和相关元素
        //2 绑定事件
        //3 书写事件驱动程序
        
        var inp2 = document.getElementById("inp2");
        var lab = document.getElementsByTagName("label")[0];
        //输入事件,文字的输入和删除都会触动这个事件
        inp2.oninput = function( ){
            if(this.value===" ";){
                lab.className="show";
            }else{
                lab.className="hide";
            }
        }

    </script>

</body>
</html>


```