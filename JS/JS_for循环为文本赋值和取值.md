## forѭ��Ϊ�ı���ֵ��ȡֵ
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

    <button>��ֵ</button><br><br>
    <button>ȡֵ</button><br><br>

    <script>
       //˼·:forѭ����ֵ
       var inpArr=document.getElementsByTagName("input");
       var btnArr=document.getElementsByTagName("button");
       
       //��ֵ
        btnArr[0].onclick=function( ){
            for(var i=0;i<inpArr.length;i++){
                inpArr[i].value=i;
            }
        }
       //ȡֵ
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