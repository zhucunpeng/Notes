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
        }
        .box {
            width: 500px;
            height: 400px;
            border: 1px solid #ccc;
            margin: 100px auto;
            overflow: hidden;
        }
        ul {
            width: 600px;
            height: 40px;
            margin-left: -1px;
            list-style: none;
        }
        li {
            float: left;
            width: 101px;
            height: 40px;
            text-align: center;
            font: 600 18px/40px "simsun";
            background-color: pink;
            cursor: pointer;
        }
        span {
            display: none;
            width: 500px;
            height: 360px;
            background-color: yellow;
            text-align: center;
            font: 700 150px/360px "simsun";
        }
        .show {
            display: block;
        }
        .current {
            background-color: yellow;
        }
    </style>
</head>
<body>

    <div class="box">
        <ul>
            <li class="current">Ь��</li>
            <li>����</li>
            <li>ñ��</li>
            <li>����</li>
            <li>ȹ��</li>
        </ul>
        <span class="show">Ь��</span>
        <span>����</span>
        <span>ñ��</span>
        <span>����</span>
        <span>ȹ��</span>
    </div>


    <div class="box">
        <ul>
            <li class="current">Ь��</li>
            <li>����</li>
            <li>ñ��</li>
            <li>����</li>
            <li>ȹ��</li>
        </ul>
        <span class="show">Ь��</span>
        <span>����</span>
        <span>ñ��</span>
        <span>����</span>
        <span>ȹ��</span>
    </div>

    <div class="box">
        <ul>
            <li class="current">Ь��</li>
            <li>����</li>
            <li>ñ��</li>
            <li>����</li>
            <li>ȹ��</li>
        </ul>
        <span class="show">Ь��</span>
        <span>����</span>
        <span>ñ��</span>
        <span>����</span>
        <span>ȹ��</span>
    </div>

</body>
</html>
```

* ����һ

```
<script>
            //�������ŵ������li�ϣ�li�����ɫ(�����)����Ӧ��spanҲ��ʾ����(�����);
            //˼·��1.�������ӡ�   2.��������ֵ��ʾ���ӡ�
            //���裺
            //1.��ȡ�¼�Դ�����Ԫ��
            //2.���¼�
            //3.��д�¼�������������˼�룩
            
            //1.��ȡ�¼�Դ�����Ԫ��
            var boxArr = document.getElementsByClassName("box");
            //��������
            for(var i=0;i<boxArr.length;i++){
                fn(boxArr[i]);
            }
    
            //������װ
            function fn(ele){
                var liArr = ele.getElementsByTagName("li");
                var spanArr = ele.getElementsByTagName("span");
                //2.���¼���ѭ���󶨣�
                for(var i=0;i<liArr.length;i++){
                    //������ֵ(�Զ�������)
                    liArr[i].setAttribute("index",i);
                    liArr[i].onmouseover = function () {
                        //3.��д�¼�������������˼�룩
                        //1.�������ӡ�   2.��������ֵ��ʾ���ӡ�(����˼��)
                        for(var j=0;j<liArr.length;j++){
                            liArr[j].removeAttribute("class");
                            spanArr[j].removeAttribute("class");
                        }
                        this.setAttribute("class","current");
                        spanArr[this.getAttribute("index")].setAttribute("class","show");
                    }
                }
            }
    </script>
```

* ������

```
<script type="text/javascript">
    var boxArr = document.getElementsByClassName("box")
    for (var i = 0; i < boxArr.length; i++) {
        fn(boxArr[i]);
    }
    function fn(ele) {
        var liArr = ele.getElementsByTagName("li");
        var spanArr = ele.getElementsByTagName("span");

        for (var i = 0; i < liArr.length; i++) {
            liArr[i].index = i;
            liArr[i].onclick=function(){
                for (var j = 0; j < liArr.length; j++) {
                    liArr[j].className = '';
                    spanArr[j].className = '';
                }
                this.className = 'current';
                spanArr[this.index].className = 'show';
        // console.log(1);
            }

        }
    }

</script>

```
