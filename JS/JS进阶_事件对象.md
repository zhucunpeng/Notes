# **�¼�����(event)**
## 1.1�������
> ���е��������֧��event���󣬵�֧�ֵķ�ʽ��ͬ
��ͨ�����֧�� event�����Σ����������
ie 678 ֧�� window.event���޲Σ����ã�
�ܽ᣺����һ���¼��е����ö����ڲ�װ�˺ܶ���������¼��������Ϣ��

## 1.2 �¼�����Ĳ���(event�Ļ�ȡ)
- IE678�У�window.event 
- �ڻ���ȸ��У�event���ߣ����¼��󶨵ĺ����У��ӲΣ������������event.
    + Box.onclick = function (aaa){   aaa����event     }

## 1.3 ���ݻ�ȡ��ʽ�����֣�
- ��д����ֱ��ʹ��event;
- д����������Ϊevent....var event  = event || window.event;(��Ҫ������)

## 1.4 event����
- pageX    �������ڸ���ҳ��ˮƽλ�ã�ie�ޣ�
- pageY    �������ڸ���ҳ�Ĵ�ֱλ�ã�ie�ޣ�
- screenX  �������ڸ���Ļ��ˮƽλ��
- screenY  �������ڸ���Ļ�Ĵ�ֱλ��
- clientX  �������ڸ���ҳ��ˮƽλ�� ����ǰ�ɼ�����
- clientY  �������ڸ���ҳ�Ĵ�ֱλ��
- bubbles  ���ز���ֵ��ָʾ�¼��Ƿ��������¼����͡�
- button   ���ص��¼�������ʱ���ĸ���갴ť�������
- timeStamp �����¼����ɵ����ں�ʱ�䡣
- target   ���¼������͵��Ķ���
- type     �¼�������

## 1.5 creenX��pageX��clientX������
- PageY/pageX: ���λ��������ҳҳ��Ķ�������ಿ�ֵľ��롣��ҳ�棩
- ScreenY/screenX: ���λ����Ļ���Ϸ������ľ��롣����Ļ��
- ClientX/clientY: ���λ������������Ͷ����ľ��롣���������С��λ�ã�
- ![](leanote://file/getImage?fileId=584101fb334ed27670000000)

## 1.6 PageY��pageX�ļ���д��������Ҫ��
> 
��ҳ��λ�þ͵��� = ���ü���+��������
pageY/pageX=event.clientY/clientX+scroll().top/scroll().left

## 1.7 �����קЧ��  �����¼�
- onmouseover  ��꾭��
- onmouseenter 
- onmouseleave
- onmouseout  ����뿪
- onmousedown  ��갴��
- onmouseup  ��굯��
- onmousemove  ����ƶ���1pxҲ����
- ע�⣺
> onmouseover��onmouseout�¼�����һ�����ӣ���Ԫ��Ҳ���ȡ����¼������������onmosueenter��onmouseleave.

## 1.8 ���ѡ�е�����
- IE9��Firefox��Safari��Chrome��Opera֧�֣�window.getSelection() 
- IE9����֧�֣�document.selection 
- ����д����
> window.getSelection?window.getSelection().removeAllRanges():document.selection.empty();

## 1.9 ģ�ⴹֱ�������ھ�
- ��̬���ù������ĸ߶� scrollBarHeight = 
�� �����ĸ߶� / ���ݵĸ߶�*�����ĸ߶� ��
- ����������һ��    �����ƶ��ľ���
(���ݵĸ߶� - �����ĸ߶�)   / (�����ĸ߶� - �������ĸ߶�)* �������ƶ��ľ���


