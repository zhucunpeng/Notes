# **�������__client����**
## 1.1 ��Ҫ��Ա
1. clientWidth	��ȡ��ҳ���������ȣ������÷���
clientHeight  ��ȡ��ҳ��������߶ȣ������÷���
    + �����߲�ͬ�����岻ͬ��
    + ���ӵ��ã�ָ���ӱ���
    + body/html���ã����������С��	
2. clientX  ������������������루event���ã�
clientY ��������������ϲ���루event���ã�
3. clientTop/clientLeft ���ӵ�border���

## 1.2	�������������������ܽᣩ
- Width��height
    + clientWidth  = width  + padding
    + clientHeight  = height + padding
    + offsetWidth  = width  + padding + border
    + offsetHeight  = height + padding + border
    + scrollWidth   = ���ݿ�ȣ�������border��
    + scrollHeight  = ���ݸ߶ȣ�������border��
    IE567�߶ȿ��ԱȺ���С��IE8+����ȸ費�ܱȺ���С
- top��left
    + offsetTop/offsetLeft ��
        * �����ߣ�����Ԫ�ء�(����Ϊ��)
        * �����ã����븸ϵ�����д��ж�λ�ľ��롣
    + scrollTop/scrollLeft:(����Ҳ���Ե��ã������й�����)
        * �����ߣ�document.body.scrollTop/.....(window)
        * �����ã�������޷���ʾ�Ĳ��֣�����ȥ�Ĳ��֣���
    + clientY/clientX:��clientTop/clientLeft ֵ����border��
        * �����ߣ�event.clientX(event)
        * �����ã��������������������ľ��루���ϣ���

## 1.3 client����֮:���������/�߶�(��������)
- ie9�������ϵİ汾
window.innerWidth/Height  
- ��׼ģʽ����DTD������CSS1Compat����
document.documentElement.clientWidth
document.documentElement.clientHeight
- ����ģʽ ��û��DTD��
document.body.clientWidth
document.body.clientHeight

## 1.4 �¼��ܽ�
onresize �¼����ڴ��ڻ��ܱ�������Сʱ����

- window.onscroll        	��Ļ����
- window.onresize      	�������С�仯
- window.onload	         ҳ��������
- div.onmousemove    		����ں������ƶ�
		��ע�⣺���Ǻ����ƶ���������
- onmouseup/onmousedown  ==  onclick

## 1.5 �����Ļ���
> window.screen.width
�ֱ�������Ļͼ��ľ��ܶȣ�ָ��ʾ��������ʾ�������ж��١�
���ǵĵ���һ�㣺
����1280�����ص㣬
����960�����ص㡣

        