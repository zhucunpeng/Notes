## JavaScript实现页面截图的类库 [html2canvas](https://github.com/niklasvh/html2canvas)

- 使用html2canvas实现浏览器截图,可以参考博客资料[http://www.cnblogs.com/yanweidie/p/5203943.html](http://www.cnblogs.com/yanweidie/p/5203943.html)
- 官方资料gitHub:[https://github.com/niklasvh/html2canvas](https://github.com/niklasvh/html2canvas)
- 在线检测浏览器兼容性:[http://deerface.sinaapp.com/](http://deerface.sinaapp.com/)

-  主要是让用户调用时能够自定义需要截取Dom对象的宽和高，现在调用方式如下

```
$("#btn_screen").on("click", function () {               
                html2canvas($("#tbl_exception"), {
                    height: $("#tbl_exception").outerHeight() + 20,
                    onrendered: function (canvas) {
                        var url = canvas.toDataURL();
                        //以下代码为下载此图片功能
                        var triggerDownload = $("<a>").attr("href", url).attr("download", getNowFormatDate()+"异常信息.png").appendTo("body");
                        triggerDownload[0].click();
                        triggerDownload.remove();
                    }
                });
            });
```


- 这是 一个网页截图并下载的小案例

```
<!DOCTYPE html>
<html>
    <!--此网页演示了html2canvas网页截图下载 --> 
    <head>
        <!-- base.js实际上是jquery库,html2canvas.js是html2canvas自带的js库 -->
        <script type="text/javascript" src="http://html2canvas.hertzen.com/build/html2canvas.js"></script>
        <script type="text/javascript" src="http://www.boolaw.com/tpl/default/js/jquery-1.8.3.min.js"></script>
        <title>html2canvas网页截图</title>
        <meta http-equiv="keywords" content="keyword1,keyword2,keyword3">
        <meta http-equiv="description" content="this is my page">
        <meta http-equiv="content-type" content="text/html; charset=UTF-8">
        <!--<link rel="stylesheet" type="text/css" href="./styles.css">-->
        <!--需要注意的是,这里一定要等待js库和网页加载完毕后再执行函数  -->
        <!-- html2canvas()中,第一个参数是要截图的Dom对象，第二个参数时渲染完成后回调的canvas对象。  -->        
        <script type="text/javascript">
            $(function(){   
                print();
            });
            function print(){   
                html2canvas( $("#canv") ,{          
                    onrendered: function(canvas){
                        $('#down_button').attr( 'href' , canvas.toDataURL() ) ;
                        $('#down_button').attr( 'download' , 'myjobdeer.png' ) ;
                        //$('#down_button').css('display','inline-block');
                        var html_canvas = canvas.toDataURL();
                        $.post('', {order_id:1,type_id:2,html_canvas:html_canvas}, function(json){
                        }, 'json');
                    }
                });
            }
        </script>
        <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
    </head>
    <body>
        <div id="canv">
        此网页演示了html2canvas截图后将截图后的网页追加到了原网页之上        <br>        <br>
        这里可以看作是边界线      <hr/>
        </div>
        <a type="button" id="down_button">下载</a>
    <?php
    if(isset($_POST['html_canvas'])){
    $order_id = $_POST['order_id'];
    $type_id = $_POST['type_id'];
    $html_canvas = $_POST['html_canvas'];
    $image = base64_decode(substr($html_canvas, 22));
    header('Content-Type: image/png');
    $filename =  $order_id.'-'.$type_id.".png";
    $fp = fopen($filename, 'w');
    fwrite($fp, $image);
    fclose($fp);
    }
    
    ?>
    </body>
</html>


```
