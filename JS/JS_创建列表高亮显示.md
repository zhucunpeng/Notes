##�����б������ʾ
```
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
    <style>
        li {
            cursor: pointer;
        }
    </style>
</head>
<body>
    <button>�����б�</button>
    <ul></ul>

    <script>
        //���󣺵���б�����Ĵ���Ů��Ȼ�����ŵ�˭���棬˭������ʾ��
        //˼·������һ�����飬������ݡ�����forѭ������li��ǩ��������ݣ�������ʾ��
        //���裺��ָ�����ٸ�Ԫ�صĴ��������forѭ����
        //������
        var btn = document.getElementsByTagName("button")[0];
        //��ȡ���Ԫ�ز���������
        var arr = ["�Ѿ�����","��ʩ�ɴ","�������","��������"];
        var ul = document.getElementsByTagName("ul")[0];
        btn.onclick = function () {
//            ul.innerHTML = "";
            for(var i=0;i<arr.length;i++){
                //����liԪ��
                var newLi = document.createElement("li");
               newLi.innerHTML += "<li>"+arr[i]+"</li>";
                //��ӵ�ul��
                ul.appendChild(newLi);
            }
            //��ȡ���е�li��ǩȻ��Ϊ�����¼�������˼�룬������ʾ
            var liArr = ul.children;
            //Ϊ���е�li���¼�
            for(var i=0;i<liArr.length;i++){
                liArr[i].onmouseover = function () {
                    //����˼�룬������ʾ
                    for(var j=0;j<liArr.length;j++){
                        liArr[j].style.backgroundColor = "";
                    }
                    this.style.backgroundColor = "red";
                }
            }
        }


    </script>


</body>
</html>
```