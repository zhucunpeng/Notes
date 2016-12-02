# **�������__scroll����**
## 1 Scroll�������
### 1.1 ScrollWidth��scrollHeight��������border��margin��
> scrollWidth = width + padding;

- �����ӵĿ�ߡ��������ߣ��ڵ�Ԫ�ء����ԡ���
- �������ݵĿ�ߡ�����������ݳ����ˣ���ʾ���ݵĸ߶�;�������Ǻ��ӱ���߶ȣ�
- IE567�߶ȿ��ԱȺ���С�� IE8+����ȸ費�ܱȺ���С

### 1.2 scrollTop��scrollLeft
> ��ҳ����������ڵ���ͷ������߲��֡�����ȥ��ͷ������߲��֡�

- ���м���������
    +  δ���� DTD���ȸ�ֻ��ʶ����
    document.body.scrollTop
    + �Ѿ�����DTD��IE678ֻ��ʶ����
   document.documentElement.scrollTop
    + ���/�ȸ�/ie9+����֧�ֵ�
   window.pageYOffset
- ����д��
```
var aaa = window.pageYOffset || document.documentElement.scrollTop || document.body.scrollTop || 0;
```

## 1.3 ��ȡtitle��body��head��html��ǩ
- document.title --- �ĵ����⣻
- document.head --- �ĵ���ͷ��ǩ
- document.body --- �ĵ���body��ǩ��
- document.documentElement --- �������Ҫ,����ʾ�ĵ���html��ǩ��Ҳ����˵�������ṹ���е�html��ǩ������ͨ��document.html ȥ���ʵģ�����document.documentElement ��

## 1.5 scroll�����ķ�װ
```
function scroll(){
            //���������Դ��ڣ���ô����ֵӦ����0-�����
            //���û�з���ֵ��undefined��
            //ֻҪ�жϲ���undefined�Ϳ��Ե��ô˷���
            //��ϰʹ�ô��ַ�װ
            if(window.pageYOffset !== undefined){
//                var json = {
//                    "top": window.pageYOffset,
//                    "left": window.pageXOffset
//                };
//                return json;
                return {
                    "top": window.pageYOffset,
                    "left": window.pageXOffset
                };
            }else if(document.compatMode === "CSS1Compat"){
                return {
                    "top": document.documentElement.scrollTop,
                    "left": document.documentElement.scrollLeft
                };
            }else{
                return {
                    "top": document.body.scrollTop,
                    "left": document.body.scrollLeft
                };
            }

            �򵥷�װ��ʵ�ʹ���ʹ�ã�
           return {
               "top": window.pageYOffset || document.body.scrollTop || document.documentElement.scrollTop,
               "left":  window.pageXOffset || document.body.scrollLeft || document.documentElement.scrollLeft
           }
        }

```

## 1.6�ж�ҳ����û��DTD
- document.compatMode === "BackCompat"
- BackCompat  δ����
- CSS1Compat  �Ѿ�����
IE678Ĭ��ʶ��CSS1Compat ��������û��dtd
**ע���Сд**
## 1.7 onscroll�¼�
ֻҪҳ����������������ң��������£�����ֻ��1px�����ᴥ������¼�
## 1.8 ��Ļ��ת
- window.scrollTo 
�����ɰ����ݹ�����ָ�������ꡣ
- ��ʽ��scrollTo(xpos,ypos)
    + xpos	���衣Ҫ�ڴ����ĵ���ʾ�����Ͻ���ʾ���ĵ��� x ���ꡣ
    + ypos	���衣Ҫ�ڴ����ĵ���ʾ�����Ͻ���ʾ���ĵ��� y ����







