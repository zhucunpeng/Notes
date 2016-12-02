# jQ_Tab���л�
## ��Ҫ����jQuery-1.11.1.js
```
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
    <style type="text/css">
        * {
            margin: 0;
            padding: 0;
        }
        ul {
            list-style: none;
        }
        .wrapper {
            width: 1000px;
            height: 475px;
            margin: 0 auto;
            margin-top: 100px;
        }

        .tab {
            border: 1px solid #ddd;
            border-bottom: 0;
            height: 36px;
            width: 320px;
        }

        .tab li {
            position: relative;
            float: left;
            width: 80px;
            height: 34px;
            line-height: 34px;
            text-align: center;
            cursor: pointer;
            border-top: 4px solid #fff;
        }

        .tab span {
            position: absolute;
            right: 0;
            top: 10px;
            background: #ddd;
            width: 1px;
            height: 14px;
            overflow: hidden;
        }

        .products {
            width: 1002px;
            border: 1px solid #ddd;
            height: 476px;
        }

        .products .main {
            float: left;
            display: none;
        }
        .products .main a{
            line-height: 300px;
            font-size: 100px;
        }

        .products .main.selected {
            display: block;
        }

        .tab li.active {
            border-color: red;
            border-bottom: 0;
        }

    </style>
    <script src="../jquery-1.11.1.js"></script>
    <script>
        jQuery(window).ready(function () {
            //����:���ŵ��Ǹ�li�ϣ��ø�li���active�࣬����Ķ�Ӧ��.main��div���selected
            $(".tab>li").mouseenter(function () {
                //�����жϣ���ǰ��li���active�࣬������ɾ��active��
                $(this).addClass("active").siblings("li").removeClass("active");
                //��Ӧ����ֵ��div���selected�࣬������ɾ��selected��
                $(".products>div").eq($(this).index()).addClass("selected").siblings("div").removeClass("selected");
            });
        });
    </script>
</head>
<body>
    <div class="wrapper">
        <ul class="tab">
            <li class="tab-item active">���ʴ���<span>��</span></li>
            <li class="tab-item">��ױ����<span>��</span></li>
            <li class="tab-item">�����Ʒ<span>��</span></li>
            <li class="tab-item">��ʿ��Ʒ</li>
        </ul>
        <div class="products">
            <div class="main selected">
                <a href="###">���ʴ���</a>
            </div>
            <div class="main">
                <a href="###">��ױ����</a>
            </div>
            <div class="main">
                <a href="###">�����Ʒ</a>
            </div>
            <div class="main">
                <a href="###">��ʿ��Ʒ</a>
            </div>
        </div>
    </div>
    
</body>
</html>
```