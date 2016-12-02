# jQ_ȫѡ��ѡ
## ��Ҫ����jQuery-1.11.1.js

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

        .wrap {
            width: 300px;
            margin: 100px auto 0;
        }

        table {
            border-collapse: collapse;
            border-spacing: 0;
            border: 1px solid #c0c0c0;
        }

        th,
        td {
            border: 1px solid #d0d0d0;
            color: #404060;
            padding: 10px;
        }

        th {
            background-color: #09c;
            font: bold 16px "΢���ź�";
            color: #fff;
        }

        td {
            font: 14px "΢���ź�";
        }

        tbody tr {
            background-color: #f0f0f0;
        }

        tbody tr:hover {
            cursor: pointer;
            background-color: #fafafa;
        }
    </style>
    <script src="jquery-1.11.1.js"></script>
    <script>
        $(function () {
            //����1���������Ķ�ѡ��ť����������ж�ѡ��ť���������һ��
            //����2���������Ķ�ѡ��ť���ж���������ж�ѡ��ť���Ƿ�ȫ����ѡ��ֻ��ȫ����ѡ������Ĳű�ѡ��


            //����1���������Ķ�ѡ��ť����������ж�ѡ��ť���������һ��
            //���裺���¼���ֱ������������а�ť������İ�ť����ֵһģһ��
            $("#j_cbAll").click(function () {
                //ֱ������������а�ť������İ�ť����ֵһģһ��
                $("#j_tb input:checkbox").prop("checked",$(this).prop("checked"));
            });

            //����2���������Ķ�ѡ��ť���ж���������ж�ѡ��ť���Ƿ�ȫ����ѡ��ֻ��ȫ����ѡ������Ĳű�ѡ��//����2���������Ķ�ѡ��ť���ж���������ж�ѡ��ť���Ƿ�ȫ����ѡ��ֻ��ȫ����ѡ������Ĳű�ѡ��
            $("#j_tb input:checkbox").click(function () {
                //�жϣ�ֻ�����ж���ѡ��������Ĳű�ѡ��
                //�����㣺����checked���Եı�ǩ��checkbox����һ�����ʱ��
                if($("#j_tb input:checkbox").length === $("#j_tb input:checked").length){
                    //ֻ�����еĶ���checked���ԣ�����Ĳű�ѡ��
                    $("#j_cbAll").prop("checked",true);
                }else{
                    $("#j_cbAll").prop("checked",false);
                }
            });


        })
    </script>
</head>

<body>
    <div class="wrap">
        <table>
            <thead>
                <tr>
                    <th>
                        <input type="checkbox" id="j_cbAll"/>
                    </th>
                    <th>�γ�����</th>
                    <th>����ѧԺ</th>
                </tr>
            </thead>
            <tbody id="j_tb">
                <tr>
                    <td>
                        <input type="checkbox"/>
                    </td>
                    <td>JavaScript</td>
                    <td>ǰ�����ƶ�����ѧԺ</td>
                </tr>
                <tr>
                    <td>
                        <input type="checkbox"/>
                    </td>
                    <td>css</td>
                    <td>ǰ�����ƶ�����ѧԺ</td>
                </tr>
                <tr>
                    <td>
                        <input type="checkbox"/>
                    </td>
                    <td>html</td>
                    <td>ǰ�����ƶ�����ѧԺ</td>
                </tr>
                <tr>
                    <td>
                        <input type="checkbox"/>
                    </td>
                    <td>jQuery</td>
                    <td>ǰ�����ƶ�����ѧԺ</td>
                </tr>
            </tbody>
        </table>
    </div>
</body>

</html>

```