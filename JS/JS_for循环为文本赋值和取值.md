## for循环为文本赋值和取值
```
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
</head>
<body>
    <input type="text"/><br><br>
    <input type="text"/><br><br>
    <input type="text"/><br><br>
    <input type="text"/><br><br>
    <input type="text"/><br><br>
    <input type="text"/><br><br>

    <button>赋值</button><br><br>
    <button>取值</button><br><br>

    <script>
       //思路:for循环赋值
       var inpArr=document.getElementsByTagName("input");
       var btnArr=document.getElementsByTagName("button");
       
       //赋值
        btnArr[0].onclick=function( ){
            for(var i=0;i<inpArr.length;i++){
                inpArr[i].value=i;
            }
        }
       //取值
        btnArr[1].onclick=function( ){
            var newArr=[];
            for(var i=0;i<inpArr.length;i++){
                newArr.push(inpArr[i].value);
            }
            console.log(newArr.join(" "));
        }

    </script>
</body>
</html>
```