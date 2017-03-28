## JavaScript实现页面截图的类库 [html2canvas](https://github.com/niklasvh/html2canvas)

- 使用html2canvas实现浏览器截图,可以参考博客资料[http://www.cnblogs.com/yanweidie/p/5203943.html](http://www.cnblogs.com/yanweidie/p/5203943.html)
- 官方资料gitHub:[https://github.com/niklasvh/html2canvas](https://github.com/niklasvh/html2canvas)
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
