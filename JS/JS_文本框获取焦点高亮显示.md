##�ı����ȡ���������ʾ
```
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
    <style>
        input {
            display: block;
        }
    </style>
</head>
<body>
<ul>
    <input type="text"/>
    <input type="text"/>
    <input type="text"/>
    <input type="text"/>
    <input type="text"/>
    <button>����</button>
</ul>
<script>
    //���󣺵�����ð�ť�������е�input��ǩ��ȡ����������ʾ
    //���裺
    //1.��ȡ�¼�Դ
    //2.���¼�
    //3.��д�¼���������

    //1.��ȡ�¼�Դ
    var inpArr = document.getElementsByTagName("input");
    var button = inpArr[inpArr.length-1].nextElementSibling || inpArr[inpArr.length-1].nextSibling ;
    //2.���¼�
    button.onclick = function () {
        //3.��д�¼���������
        for(var i=0;i<inpArr.length;i++){
            //��button��ť������Ժ����е�input��ǩ�����¼���onfocus�¼�
            inpArr[i].onfocus = function () {
                this.style.border = "2px solid red";
                this.style.backgroundColor = "#ccc";
            }
            //��onblur�¼���ȡ����ʽ
            inpArr[i].onblur = function () {
                this.style.border = "";
                this.style.backgroundColor = "";
            }
        }
    }



</script>
</body>
</html>
```