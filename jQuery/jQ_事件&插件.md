# jQuery�¼�
## 1. jQuery�¼�����
> jQuery���¼����ƣ�ָ���ǣ�jQuery��JavaScript����DOM�¼��ķ�װ�������ˣ��¼��󶨡��¼�����¼�����

### 1.1 jQuery�¼���
> ���¼��� >> bind�¼��� >> delegate�¼��� >> on���ص㡿

- ���¼��󶨣�
    + click(handler) 			�����¼�
    + blur(handler) 			ʧȥ�����¼�
    + mouseenter(handler) 		�������¼�
    + mouseleave(handler)		����뿪�¼�
    + dbclick(handler) 			˫���¼�
    + change(handler)           �ı��¼����磺�ı���ֵ�ı䣬�����б�ֵ�ı��
    + focus(handler) 			��ý����¼�
    + keydown(handler) 			���̰����¼�
    + �����ο���http://www.w3school.com.cn/jquery/jquery_ref_events.asp

- bind��ʽ�����Ƽ���1.7�Ժ��jQuery�汾��onȡ����
    + ���ã���ƥ�䵽��Ԫ��ֱ�Ӱ��¼�
    + �ȼ��¼��󶨷�ʽ�����ƣ�
    ����ͬʱ�󶨶���¼������磺bind(��mouseenter  mouseleave��, function(){})
    + ȱ�㣺Ҫ���¼���Ԫ�ر�������ĵ��С�
```
// �󶨵����¼��������
��һ���������¼�����
�ڶ����������¼��������
$("p").bind("click mouseenter", function(e){
    //�¼���Ӧ����
});
```

- delegate��ʽ���ص㣺���ܸߣ�֧�ֶ�̬������Ԫ�أ�
    + ���ã���ƥ�䵽��Ԫ�ذ��¼�����֧�ֶ�̬������Ԫ����Ч
    + ��һ��������selector��Ҫ���¼���Ԫ��
    + �ڶ����������¼�����
    + �������������¼�������
    + ��ǰ���ַ�ʽ�������ƣ������¼��󶨴������Ч�ʣ�֧�ֶ�̬����������Ԫ�ذ��¼���
```
$(".parentBox").delegate("p", "click", function(){
    //Ϊ .parentBox��������е�p��ǩ���¼�
});
```

- on��ʽ
> �����ִ��ķ�ʽ������zepto(�ƶ�������jQuery��һ����)��ǿ�ҽ���ʹ�õķ�ʽ�����ص㣩jQuery1.7�汾��jQuery��onͳһ�����е��¼�����ķ���

    + ���ã���ƥ���Ԫ�ذ��¼����������������а��¼���ʽ���ŵ�
    + �﷨��
    ��һ��������events�����¼������ƿ������ɿո�ָ��Ķ���¼�����׼�¼������Զ����¼���
    �ڶ���������selector, ִ���¼��ĺ��Ԫ��
    ������������data�����ݸ������������ݣ��¼�������ʱ��ͨ��event.data��ʹ��
    ���ĸ�������handler���¼�������
```
$(selector).on(events[,selector][,data],handler);
$(selector).on("click mouseenter","span",{"name":111}, function (event) {
    alert(event.data.name);
});
//��ʾ��$(selector)�󶨶���¼����������������ڲ�Ԫ��span����ִ������¼�������111
$(selector).on( "click",��span��, function() {});

```

## 1.2 jQuery�¼����
- nbind() ��ʽ
���ã���� bind��ʽ�󶨵��¼�
```
$(selector).unbind(); //������е��¼�
$(selector).unbind(��click��); //���ָ�����¼�
```

- undelegate() ��ʽ
���ã����delegate��ʽ�󶨵��¼�
```
$( selector ).undelegate(); //������е�delegate�¼�
$( selector).undelegate( ��click�� ); //������е�click�¼�
```

- off���on��ʽ�󶨵��¼����ص㣩
```
// ���ƥ��Ԫ�ص������¼�
$(selector).off();
// ���ƥ��Ԫ�ص�����click�¼�
$(selector).off(��click��);
// ������д����click�¼���Ԫ�ر�����¼����ᱻ��� 
$(selector).off( ��click��, ��**�� ); 
```

## 1.3 �¼�����
- ���¼�����
    ```$(selector).click(); //���� click�¼�```

- trigger���������¼��������������Ϊ
```
//�¼�����(2)(�����������Ϊ)(ִ�г��򣬴����¼�)
$(document).click(function () {
   $("input").trigger("focus");
});
```

- triggerHandler���� �¼���Ӧ�������������������Ϊ
    ����:�ı����ý����Ĭ����Ϊ
```
//�¼�����(3)(�������������Ϊ)(ִֻ�г��򣬲������¼�)
$(document).click(function () {
    $("input").triggerHandler("focus");
});
```

## 1.4 jQuery�¼��������
- event.data 					���ݸ��¼��������Ķ�������
- event.currentTarget 			��ͬ��this����ǰDOM����
- event.pageX 					���������ĵ��󲿱�Ե��λ��
- event.target 					�����¼�Դ����һ��===this
- event.stopPropagation()��	    ��ֹ�¼�ð��
- event.preventDefault(); 	    ��ֹĬ����Ϊ
- event.type 					�¼����ͣ�click��dbclick��
- event.which 					���İ������ͣ���1 ��2 ��3
- event.keyCode				    ���̰�������

## 1.5 jQuery����
- ��ʽ���
��ʽ���ԭ��return this;
ͨ������£�ֻ�����ò������ܰ���ʽ���������ȥ����Ϊ��ȡ������ʱ�򣬻᷵�ػ�ȡ������Ӧ��ֵ���޷����� this��
end(); // ������ǰ�������һ�ι��˲��������ҷ���ƥ��Ԫ��֮ǰ��״̬��
- ��ʽ����
��ʽ��������˼�ǣ��ڷ������ڲ���Ϊƥ�䵽������Ԫ�ؽ���ѭ��������ִ����Ӧ�ķ����������������ٽ���ѭ���������ǵĲ������������ǵ��á�
�����ȡ���Ƕ�Ԫ�ص�ֵ���󲿷�����·��ص��ǵ�һ��Ԫ�ص�ֵ��
- each����
> ������ʽ������Ϊʲô��Ҫʹ��each����������
�󲿷�������ǲ���Ҫʹ��each�����ģ���ΪjQuery����ʽ�������ԡ�
���Ҫ��ÿ��Ԫ������ͬ�Ĵ�����ʱ����õ���each����

    + ���ã�����jQuery���󼯺ϣ�Ϊÿ��ƥ���Ԫ��ִ��һ������
    + ����һ��ʾ��ǰԪ��������ƥ��Ԫ���е�������
    + ��������ʾ��ǰԪ�أ�DOM����
    $(selector).each(function(index,element){});
    Element��һ�� js������Ҫת����jquery����

- ��⹲��
�˴���⹲��ָ���ǣ�jQueryռ����$ ��jQuery����������������ͬһ��ҳ����������jQuery���js�⣬�������õ������⣨���������汾��jQuery�⣩��Ҳ�õ���$����jQuery��������������ô��Ҫ��֤ÿ���ⶼ������ʹ�ã���ʱ������˶�⹲������⡣
```
// ģ������Ŀ�ʹ���� $ �������
// ��ʱ������jQuery������˳�ͻ
var $ = { name : ��itecast�� };
```
�����ʽ��
```
���ã���jQuery�ͷŶ�$�Ŀ���Ȩ�����������ܹ�ʹ��$���ţ��ﵽ��⹲���Ŀ�ġ��˺�ֻ��ʹ��jQuery������jQuery�ṩ�ķ���
$.noConflict();  //true������������������ֵ���µĵ��÷���
```

## 1.6 jQuery�������
jQuery���js�⣬��Ȼ����ǿ�󣬵�Ҳ��������㵽�������еĹ��ܡ�
jQuery��ͨ������ķ�ʽ������չ���Ĺ��ܣ�
������Ҫĳ�������ʱ������ԡ���װ����jQuery���棬Ȼ��ʹ�á�
���㲻����Ҫ������������Ϳ��Դ�jQuery�ϡ�ж�ء�����

- ���������
jQuery.color.js
animate()�Զ��嶯������֧�ֱ����Ķ���Ч��
animate����֧�ֵ������б�
jQuery.lazyload.js
ʹ�ò��裺
1.	����jQuery�ļ�
2.	������
3.	ʹ�ò��
- �������
��δ���jQuery�����
http://learn.jquery.com/plugins/basic-plugin-creation/
    + ȫ��jQuery������չ����
    $.pluginName = function() {};

    + jQuery������չ����
    $.fn. pluginName = function() {};

- jQueryUI
jQueryUIרָ��jQuery�ٷ�ά����UI����Ĳ����
�ٷ�API��http://api.jqueryui.com/category/all/
�����̳̣�jQueryUI�̳�
����ʹ��:
1. ����jQueryUI����ʽ�ļ�
2. ����jQuery
3. ����jQueryUI��js�ļ�
4. ʹ��jQueryUI����


