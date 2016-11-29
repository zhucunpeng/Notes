
## 隔行变色高亮显示

```
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
    <style>
        * {
            padding: 0;
            margin: 0;
            text-align: center;
        }

        .wrap {
            width: 500px;
            margin: 100px auto 0;
        }

        table {
            border-collapse: collapse;
            border-spacing: 0;
            border: 1px solid #c0c0c0;
            width: 500px;
        }

        th,
        td {
            border: 1px solid #d0d0d0;
            color: #404060;
            padding: 10px;
        }

        th {
            background-color: #09c;
            font: bold 16px "微软雅黑";
            color: #fff;
        }

        td {
            font: 14px "微软雅黑";
        }

        tbody tr {
            background-color: #f0f0f0;
            cursor: pointer;
        }

        .current {
            background-color: red!important;
        }
    </style>
</head>
<body>
<div class="wrap">
    <table>
        <thead>
        <tr>
            <th>序号</th>
            <th>姓名</th>
            <th>课程</th>
            <th>成绩</th>
        </tr>
        </thead>
        <tbody id="target">
        <tr>
            <td>
                1
            </td>
            <td>吕不韦</td>
            <td>语文</td>
            <td>100</td>

        </tr>
        <tr>
            <td>
                2
            </td>
            <td>吕布</td>
            <td>日语</td>
            <td>100</td>
        </tr>
        <tr>
            <td>
                3
            </td>
            <td>吕蒙</td>
            <td>营销学</td>
            <td>100</td>
        </tr>
        <tr>
            <td>
                4
            </td>
            <td>吕尚</td>
            <td>数学</td>
            <td>100</td>
        </tr>
        <tr>
            <td>
                5
            </td>
            <td>吕雉</td>
            <td>英语</td>
            <td>100</td>
        </tr>
        <tr>
            <td>
                6
            </td>
            <td>吕超</td>
            <td>体育</td>
            <td>100</td>
        </tr>
        </tbody>
    </table>
</div>

<script>
    //需求：让tr各行变色，鼠标放入tr中，高亮显示。

    //1.隔行变色。
    var tbody = document.getElementById("target");
    var trArr = tbody.children;
    //循环判断并各行赋值属性（背景色）
    for(var i = 0;i<trArr.length;i++){
        if(i%2 !==0){
            trArr[i].style.backgroundColor = "#a3a3a3";
        }else{
            trArr[i].style.backgroundColor = "#ccc";
        }

        //鼠标进入高亮显示
        //难点：鼠标移开的时候要回复原始颜色。
        //计数器（进入tr之后，立刻记录颜色，然后移开的时候使用记录好的颜色）
        var color = "";
        trArr[i].onmouseover = function(){
            //赋值之前，先把之前的颜色存起来
            color = this.style.backgroundColor;
            this.style.backgroundColor = "#fff";
        }
        trArr[i].onmouseout = function(){
            this.style.backgroundColor = color;
        }

    }

</script>

</body>
</html>
```