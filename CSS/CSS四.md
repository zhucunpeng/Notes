#**Css����**
>CSS ָ�����ʽ�� (Cascading Style Sheets)(������ʽ��)
Css����������html��ǩ�ģ��൱��ҳ�滯ױ��
##1��ҳ�沼��
###1.1 �ĵ���(��׼��)
>Ԫ�����϶��£�������ң���Ԫ�ض�ռһ�У�����Ԫ����һ������ʾ����������Ԫ�صı߿��С�
###1.2 ��������
>float:  left | right
�ص㣺
��Ԫ�ظ���֮��ռ��ԭ����λ�ã��ѱ꣩
�︡���ĺ�����һ������ʾ
������Ԫ�ظ���֮��ת��Ϊ���ڿ�Ԫ�ء������Ƽ�ʹ�ã�ת����Ԫ�����ʹ��display: inline-block;��
###1.3�������
>��������û�����ø߶ȣ�����ĺ���û�����ø���������»Ὣ�������ĸ߶ȳſ���һ���������еĺ������ø����������׼�ĵ���������������û�и߶ȣ�����ĺ��ӻ��ܵ������ĺ������档�������������������Ҫ�������

* ����������ǲ��ø�����������������Ĳ���Ӱ�졣
* ��������ķ���
clear: left  |  right  | both
�������õ�������clear:both;
 * �����ǩ��
    �����һ������Ԫ�غ���ӱ�ǩ��
    ```<div style="clear:both;"></div>```
 * ������Ԫ��ʹ��overflow:hidden;
 * αԪ���������  �Ƽ�ʹ��
```
.clearfix:after{
    content:".";
    display: block;
    height: 0;
    line-height: 0;
    visibility: hidden;
    clear:both;
}
/*����ie�����*/
.clearfix{
    zoom:1;
}
```
### 1.4 overflow
* overflw:hidden; �Ὣ���˺��ӵ����ݲõ�
* overflw:auto;�����ݳ��˺���֮�⣬���Զ����ɹ����������û�����ݳ�����֮�⣬�򲻳��ֹ�����
* overflw:scroll;������������û�г����ӣ��������ɹ�����
* overflw:visible;���ݳ��˺��ӻ���ʾ�������ɹ�����

##2��CSS��ʼ��
###2.1��Ѷ��
```
body,ol,ul,h1,h2,h3,h4,h5,h6,p,th,td,dl,dd,form,fieldset,legend,input,textarea,select{margin:0;padding:0} 
body{font:12px"����","Arial Narrow",HELVETICA;background:#fff;-webkit-text-size-adjust:100%;} 
a{color:#2d374b;text-decoration:none} 
a:hover{color:#cd0200;text-decoration:underline} 
em{font-style:normal} 
li{list-style:none} 
img{border:0;vertical-align:middle} 
table{border-collapse:collapse;border-spacing:0} 
p{word-wrap:break-word} 
```
###2.2���ˣ�
```
body,ul,ol,li,p,h1,h2,h3,h4,h5,h6,form,fieldset,table,td,img,div{margin:0;padding:0;border:0;} 
body{background:#fff;color:#333;font-size:12px; margin-top:5px;font-family:"SimSun","����","Arial Narrow";}
ul,ol{list-style-type:none;} 
select,input,img,select{vertical-align:middle;} 
a{text-decoration:none;} 
a:link{color:#009;} 
a:visited{color:#800080;} 
a:hover,a:active,a:focus{color:#c00;text-decoration:underline;} 
```

###2.3�Ա���
```
body, h1, h2, h3, h4, h5, h6, hr, p, blockquote, dl, dt, dd, ul, ol, li, pre, form, fieldset, legend, button, input, textarea, th, td { margin:0; padding:0; } 
body, button, input, select, textarea { font:12px/1.5tahoma, arial, \5b8b\4f53; } 
h1, h2, h3, h4, h5, h6{ font-size:100%; } 
address, cite, dfn, em, var { font-style:normal; } 
code, kbd, pre, samp { font-family:couriernew, courier, monospace; } 
small{ font-size:12px; } 
ul, ol { list-style:none; } 
a { text-decoration:none; } 
a:hover { text-decoration:underline; } 
sup { vertical-align:text-top; } 
sub{ vertical-align:text-bottom; } 
legend { color:#000; } 
fieldset, img { border:0; }
button, input, select, textarea { font-size:100%; } 
table { border-collapse:collapse; border-spacing:0; } 
```
 