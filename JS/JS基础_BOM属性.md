# BOM���
## 1. window����
### 1.1 window��JavaScript�Ķ�������

### 1.2 ���ж�����ȫ���������еı����ͺ�������window�����е����Ժͷ���

### 1.3 window�����µ����Ժͷ������õ�ʱ�����ʡ��window

## 2. BOM�����÷��������ö���
### 2.1 �´���=window.open(��ַ,�Ƿ��´���,�´��ڵĲ���)

* window.open(url,target,param)
* url Ҫ�򿪵ĵ�ַ
* target�´��ڵ�λ�� _blank _self _parent(�����)
* param �´��ڵ�һЩ���� ����ֵ���´��ڵľ��

������һЩ������
> name���´��ڵ����ƣ�����Ϊ��
featurse�����Կ����ַ������ڴ˿��ƴ��ڵĸ������ԣ�����֮���Զ��Ÿ�����
fullscreen= { yes/no/1/0 } �Ƿ�ȫ����Ĭ��no
channelmode= { yes/no/1/0 } �Ƿ���ʾƵ������Ĭ��no
toolbar= { yes/no/1/0 } �Ƿ���ʾ��������Ĭ��no
location= { yes/no/1/0 } �Ƿ���ʾ��ַ����Ĭ��no
directories = { yes/no/1/0 } �Ƿ���ʾת��ť��Ĭ��no
status= { yes/no/1/0 } �Ƿ���ʾ����״̬����Ĭ��no
menubar= { yes/no/1/0 } �Ƿ���ʾ�˵���Ĭ��no
scrollbars= { yes/no/1/0 } �Ƿ���ʾ��������Ĭ��yes
resizable= { yes/no/1/0 } �Ƿ񴰿ڿɵ�����С��Ĭ��no
width=number ���ڿ�ȣ����ص�λ��
height=number ���ڸ߶ȣ����ص�λ��
top=number ��������Ļ�������루���ص�λ��
left=number ��������Ļ��߾��루���ص�λ��

### 2.2 �رձ�ҳ��
```
a2.onclick = function () {
window.close();
}
```

### 2.3 location����
* a��location����
window.location
location�൱���������ַ�����Խ�url�����ɶ�����Ƭ��
* b��location���������

    * href
    * hash ����url��#��������ݣ�����#
    * host �������������˿�
    * hostname ������
    * pathname url�е�·������
    * protocol Э�� һ����http��https
    * search ��ѯ�ַ���
* c��location����ķ���

    * location.assign() �ı��������ַ���ĵ�ַ������¼����ʷ��
    * ����location.href �ͻ����assign()��һ��ʹ��location.href ����ҳ��֮�����ת
    * location.replace() �滻�������ַ���ĵ�ַ�������¼����ʷ��
    * location.reload()    ���¼���
    
### 2.4 history����

* a������
history.back()
history.go(-1) 0��ˢ��

* b��ǰ��
history.forward()
history.go(1)