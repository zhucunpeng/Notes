# **1. �����ͷ�װ**
## 1.1 �����ķ���
- ����   
    div.style.left ="500px"
- ����
- ����

## 1.2 ����ԭ��
**����δ����λ�� = �������ڵ�λ�� + ������**
> 
style.left��ֵ����offsetLeft��ȡֵ��
style.left��ȡֵ�����㣬��ȡ����ʽ�����û��ֵ���������׳���NaN��
offsetLeft��ȡֵ�ر𷽱㣬�������ֳ�number������㡣��Ϊ����ֻ���Ĳ��ܸ�ֵ��

## 1.3 ��������ԭ��
**����ԭ�� = ����λ�� + ����������Խ��ԽС��**
> 
leader=leader+(target-leader)/10;
    ����λ�� = ���ӱ���λ��+��Ŀ��λ��-���ӱ���λ�ã�/ 10��


## 1.4 ������װʵ������
```
 var btnArr = document.getElementsByTagName("button");
    var box = document.getElementsByClassName("box")[0];
    //���¼�
    btnArr[0].onclick = function () {
        //�����һ������Ҫ��������һ�����ӣ���ô���ǵķ����Ͳ�������
        //��������Ҫ���ӵڶ������������ƶ��ĺ��ӱ���
        animate(box,200);
    }
 
    function animate(ele,target){
        //Ҫ�ö�ʱ�����������ʱ��
        //һ������ֻ����һ����ʱ�����������Ļ���������������ӳ��ֶ�ʱ����ͻ
        //����ʱ������ͳ�Ϊ���ӵ�һ������
        clearInterval(ele.timer);
        //����Ҫ����Ӽ�����ǰ���������ô���ǵĲ����͵������и�
        //Ŀ��ֵ������ڵ�ǰֵȡ����Ŀ��ֵ���С�ڵ�ǰֵȡ��
        var speed = target>ele.offsetLeft?10:-10;
        ele.timer = setInterval(function () {
            //��ִ��֮ǰ�ͻ�ȡ��ǰֵ��Ŀ��ֵ֮��
            var val = target - ele.offsetLeft;
            ele.style.left = ele.offsetLeft + speed + "px";
            //Ŀ��ֵ�͵�ǰֵ֮�����С�ڲ�������ô�Ͳ�����ǰ����
            //��Ϊ���������и�������ת���ɾ���ֵ���Ƚ�
            if(Math.abs(val)<Math.abs(speed)){
                ele.style.left = target + "px";
                clearInterval(ele.timer);
            }
        },30)
    }

```

## 1.5 ����������װʵ������
```
 var��btn = document.getElementsByTagName("button")[0];
    var��div = document.getElementsByTagName("div")[0];

    var timer = null;

    btn.onclick = function () {
        //Ҫ�ö�ʱ�������嶨ʱ��
        clearInterval(timer);
        timer = setInterval(function () {
            var target = 0;
            //��������λ����أ�����Խ��ԽС....
            //   ������Ŀ��λ�úͺ�������λ�õ�ʮ��֮һ
            //���10���ص�ʱ����1����1���ص���Ŀ��λ���ƶ������ܹ�����ָ��λ�á�
            var step = (target - div.offsetLeft)/10;
            //ÿ�λ�ȡ����������ȡ������������Ͱ���step<0.4�����
            //��չ����ֵ����0��ʱ������ȡ����С��0��ʱ������ȡ����
            //step = Math.ceil(step);
            step = step>0?Math.ceil(step):Math.floor(step);
            //step = target>div.offsetLeft?Math.ceil(step):Math.floor(step);

            //����ԭ������δ����λ�� = ���ӵ�ǰ��λ��+����
            div.style.left = div.offsetLeft + step + "px";
            //����������Ŀ��λ��-��ǰλ�õľ���ֵ��С�ڲ���
            console.log(1);
            if(Math.abs(0-div.offsetLeft)<Math.abs(step)){
                div.style.left = 0+"px";
                clearInterval(timer);
            }
        },30);
    }
```
