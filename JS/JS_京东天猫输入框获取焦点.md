#������è������ȡ����
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
    ����:<input id="inp1" type="text" value="���Ǿ���"/><br><br>
    �Ա�:<label for="inp2">�����Ա�</label><input id="inp2" type="text"/><br><br>
    placeholder:<input type="text" placeholder="����placeholder"/>

    <script>
        //����:�����Ļ�ȡ����
        //˼·:������input��ť��ȡ�˲������������ɾ������,ʧȥ�����������ʾ����
        //����
        //1 ��ȡ�¼�Դ�����Ԫ��
        //2 ���¼�
        //3 ��д�¼���������
        
        //1 ��ȡ�¼�Դ�����Ԫ��
        var inp1 =document.getElementById("inp1");
        //���¼�(��ȡ�����¼�)
        inp1.onfocus=function( ){
            //�ж�,���input�����������"���Ǿ���",��ô��ֵ��ֵΪ""
            if(this.value==="���Ǿ���"){
                inp1.value="";
                }
            }
        //ʧȥ�����¼�
        inp1.onblur=function(){
            //ʧȥ������ж�,���input����Ϊ��,��ô�����ݸ�ֵΪ���Ǿ���
            if(this.value===""){
                inp1.value="���Ǿ���";
            }
        }
        
        //����:�Ա��Ļ�ȡ����
        //˼·:��input����������,label��ǩ����,��������ֱ�ɿ��ַ���,label��ʾ
        //����
        //1 ��ȡ�¼�Դ�����Ԫ��
        //2 ���¼�
        //3 ��д�¼���������
        
        var inp2 = document.getElementById("inp2");
        var lab = document.getElementsByTagName("label")[0];
        //�����¼�,���ֵ������ɾ�����ᴥ������¼�
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