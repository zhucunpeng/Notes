## 如何避免用户多次点击或恶意点击造成的多次请求
- 更多方法详细请参考博客一：[http://www.cnblogs.com/luckyXcc/p/5804650.html](http://www.cnblogs.com/luckyXcc/p/5804650.html)
- 更多方法详细请参考博客二：[http://www.jb51.net/article/77571.htm](http://www.jb51.net/article/77571.htm)
- 方法1： 小技巧

```
var isAjax=false;
$("btn").click(function(){
  if(isAjax)
  return;
  isAjax=true;
  setTimeout(function(){
    alert(123);
    isAjax=false;
  },2000);
});
刚开始为false，点击之后，为true就不执行，即不能再点击了。
执行下一句，一开始设置为true，防止其它点击，也就不会重复地点击了。即使点击多次也只会弹出一次。
```

- 方法2：用变量标识符 （定时器模拟延迟返还数据）

```
 var clickState = 0;//初始化点击状态
    $(function(){
        $('.button').click(function(){
            if( clickState == 1){
                //如果状态为1就什么都不做
            }else{
                clickState = 1;  //如果状态不是1  则添加状态 1
                setTimeout(addAjax,2000);
            }
        });
    });
    function addAjax(){
        $.ajax({
            success:function(){
                    $('.wrap').append('<div>添加</div>') ;
                    clickState = 0;
            }
        });
    }
```
- 方法3：添加html内容作为标示

```
$(function(){
        $('.button').click(function(){
            if(!!$('.hidden')[0]){

            }else{
                $('body').append('<input type="hidden" class="hidden">'); //向html中添加 input.hidden 元素作为标识符
                setTimeout(addAjax,2000);
            }
        });
    });
    function addAjax(){
        $.ajax({
            success:function(){
                    $('.wrap').append('<div>添加</div>') ;
                    $('.hidden').remove();// 返回数据后 移除该元素
            }
        });
    }
```

