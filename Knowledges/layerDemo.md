## layer使用方法官方api详见http://www.layui.com/doc/modules/layer.html
## 官方小demo参考详见：http://layer.layui.com/
## 练习小demo如下：

```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <link rel="stylesheet" type="text/css" href="bower_components/layer-v3.0.1/layer/mobile/need/layer.css">
  <title>layer</title>
  <style type="text/css">
    
  </style>
</head>
<body>
  <div id="test">欢迎使用简洁的layer</div>
  <button id="test1">小小提示层</button>
  <button id="test2">弹出一个页面层</button>
  <button id="parentIframe">弹出一个iframe层</button>
  <button id="tips">tips层</button>
  <button id="test3">测试按钮</button>
  <button id="test4">测试回调按钮</button>
</body>
</html>
<script type="text/javascript" src="bower_components/jquery/jquery.js"></script>
<script type="text/javascript" src="bower_components/layer-v3.0.1/layer/layer.js"></script>
<script type="text/javascript">
  $('#test1').on('click',function(){
    layer.msg('Hello layer');
  });
  $('#test2').on('click',function(){
    layer.open({
      type:1,
      area:['500px','360px'],
      shadeClose:true,//点击遮罩关闭
      // content:'你好啊 欢迎使用layer',
      content:$('#test'),
      // content:'</div style="padding:10px;">自定义内容</div>'
    });
  });
  $('#parentIframe').on('click',function(){
    layer.open({
      offset: ['100px', '50px'],//同时定义top、left坐标
      type:2,
      title:'iframe父子操作',
      maxmin:true,
      shadeClose:true,//点击关闭遮罩层
      area:['800px','520px'],
      // content:'iframe.html',
      content:'http://sentsin.com',

    });
  });
  $('#tips').on('click',function(){
    // layer.alert('酷毙了', {icon: 1});
    // layer.msg('不开心。。', {icon: 5});
    // layer.load(1);
    layer.open({
      tips:[4,'#f00'],//tips层的私有参数。支持上右下左四个方向，通过1-4进行方向设定。有时你还可能会定义一些颜色，可以设定tips: [1, '#c00']
      type:4,
      content:['数组第二项即吸附元素选择器或者DOM','#tips']
    });
  });
  $('#test3').on('click',function(){
    /*layer.confirm('纳尼？', {
        btn: ['按钮一', '按钮二', '按钮三'] //可以无限个按钮
        ,btn3: function(index, layero){
          //按钮【按钮三】的回调
          alert(3);
        }
      }, function(index, layero){
        //按钮【按钮一】的回调
        alert(1);
      }, function(index){
        //按钮【按钮二】的回调
        alert(2);
      });*/
      layer.open({
        content: 'test'
        ,btn: ['按钮一', '按钮二', '按钮三']
        ,yes: function(index, layero){
          //按钮【按钮一】的回调
          alert('按钮一的回调');
        },btn2: function(index, layero){
          //按钮【按钮二】的回调
          alert('按钮二的回调');
        },btn3: function(index, layero){
          //按钮【按钮三】的回调
          alert('按钮三的回调');
        }
        ,cancel: function(){ 
          //右上角关闭回调
          alert('右上角关闭的回调');
        }
      });
  });
  $('#test4').on('click',function(){
    /*layer.open({
      content: '测试回调',
      success: function(layero, index){
        console.log(layero, index);
      }
    });*/
    layer.open({
      content: '测试回调',
      yes: function(index, layero){
        //do something
        console.log(index,layero);
        layer.close(index); //如果设定了yes回调，需进行手工关闭
      }
    });       
  });
 

 
</script>

```
