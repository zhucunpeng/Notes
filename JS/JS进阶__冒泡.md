#**ð�ݻ��ƣ�event��**
## 1.1 �������
> �¼�ð��: ��һ��Ԫ���ϵ��¼���������ʱ�򣬱���˵�������һ����ť��ͬ�����¼��������Ǹ�Ԫ�ص���������Ԫ���б���������һ���̱���Ϊ�¼�ð�ݣ�����¼���ԭʼԪ�ؿ�ʼһֱð�ݵ�DOM�������ϲ㡣(BUG)
������Ӧ��һ������һ�˵�������������������飬��ȥ�������裩

- ʲô��ð�ݣ���Ԫ���¼��������������ӵ�ͬ�����¼�Ҳ�ᱻ������
- ȡ��ð�ݾ���ȡ�����ֻ��ơ�

## 1.2 �¼������׶�
> �¼������������׶��ǣ�����ð�ݺ�Ŀ��׶�

- �¼�����׶Σ��¼�������һ����ǩ��ʼ���²��ң�ֱ�������¼�Ŀ��(target)��
- �¼�ð�ݽ׶Σ��¼����¼�Ŀ��(target)��ʼ������ð��ֱ��ҳ�������һ����ǩ��

## 1.3 ð��˳��
- IE 6.0: 
div -> body -> html -> document
- ���������: 
div -> body -> html -> document -> window
> 
�������е��¼�����ð�ݡ������¼���ð�ݣ�blur��focus��load��unload��onmouseenter
onmouseleave

## 1.4 ��ֹð��
- w3c�ķ����ǣ���������ȸ衢IE11��
	event.stopPropagation()
- IE10��������ʹ�ã�event.cancelBubble = true
- ���ݴ������£�

```
  var event = event || window.event;
 if(event && event.stopPropagation){
            event.stopPropagation();
  }else{
            event.cancelBubble = true;
  }
```

## 1.5 �¼�ί��
```
//��ͨ���¼��󶨣�û�а취Ϊ�´�����Ԫ�ذ��¼�����������Ҫʹ��ð�ݵ����ԣ��¼�ί�У�
    //�¼�ί��
    ul.onclick = function (event) {
        //��ȡ�¼�������ʱ�򴫵ݹ�����ֵ
        event = event || window.event;
        var aaa = event.target?event.target:event.srcElement;
        //�жϱ�ǩ���������li��ǩ����
        if(aaa.tagName === "LI"){
            alert("����li");
        }
    }
```

## 1.6 ����ģ̬��
- �жϵ�ǰ����
- IE678    event.srcElement���¼�Դ��
- ���/�ȸ��  event.target���¼�Դ��
- ����д����ȡԪ��ID��
```
var event = event || window.event;
var targetId =  event.target ?  event.target.id : event.srcElement.id;
```

## 1.7 �������Ի�ȡ/��ֵ����
- �����Ը�ֵ�������ܻ�ȡ���ܸ�ֵ��
    + div.style.width     ������ֵ
    + div.style[��width��]  ������ֵ

- ��ȡ����ֵ����ֻ�ܻ�ȡ��
    + div.currentStyle.width;   IE678 	������ȡ
    + window.getComputedStyle(div,null).width;
    + div.currentStyle[��width��];   IE678		������ȡ
    + window.getComputedStyle(div,null)[��width��];
����1����ȡ���Ե�Ԫ�ء�
����2��αԪ�أ�C3ѧϰ��
- ���ݷ�����ȡԪ����ʽ
```
        function getStyle(ele,attr){
            if(window.getComputedStyle){
                return window.getComputedStyle(ele,null)[attr];
            }
            return ele.currentStyle[attr];
        }
```

## 1.8 ͸����
- opacity: 0.5;  ����һ��͸��.(����ȸ�IE9+)
	ȡֵ��Χ��  0-1
- filter: alpha(opacity=50);     IE678(���о�)
         ȡֵ��Χ��  0-100
