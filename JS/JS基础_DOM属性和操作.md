#DOM����
##1. �¼�
###1.1 ����
JS�����¼�����Ϊ���ĵ�һ������
###1.2 �¼���Ҫ��
>�¼�Դ���¼����¼���������

* a����ȡ�¼�Դ
    ��ȡ�¼�Դһ��5��
document.getElementById("box");
document.getElementsByTagName("div");
document.getElementsByClassName("leiming");
Ҫ�������������֣����治����
document.getElementsByName("aaa");
* b�����¼�
box.onclick = function(){ ���� };
* c����д�¼���������
�Ժ�Ҫѧϰ�Ĺ���DOM�Ĳ���

###1.3 �¼�����Щ
* a��onclick  ��굥��
* b��ondblclick ���˫��
* c��onkeyup            ���²��ͷŻ������˵��е�ѡ����ı�
* d��onchange         �ı����ݻ������˵��е�ѡ����ı�
* e��onfocus             ��ȡ���㣬��ʾ�ı���Ȼ�������
* f��onblur                ʧȥ���㣬��ʾ�ı����ʧȥ�����
* g��onmouseover    �����ͣ�������ͣ����ͼƬ�ȵ��Ϸ�
* h��onmouseout      ����Ƴ������뿪ͼƬ����������
* i��onload                ��ҳ�ĵ������¼�
* j��onunload            �ر���ҳʱ
* k��onsubmit           ���ύ�¼�
* l��onreset               ���ñ�

###1.4 onload�¼�
>ʲô�����´�������¼��أ�ҳ����أ��ı���ͼƬ����ϵ�ʱ��?
��;
js�ļ���ʱ��htmlͬ�����صġ������ʹ��Ԫ���ڶ���Ԫ��֮�䣬���ױ�����
����ҳ��������Ԫ�ؼ��������ִ��js����
window.onload����Ԥ��ʹ�ñ�ǩ�ڶ����ǩ֮ǰ��
 
##2. DOM����
###2.1 ��������?
>HTML������ϣ���Ⱦ��������ڴ��а�HTML�ĵ�������һ��DOM����getElementById�Ǻͻ�ȡ����DOM�ϵ�Ԫ���߽ڵ㣬Ȼ�������ʱ��ĵ��Ǹ�Ԫ�ص�����

###2.2 DOM(�ĵ�����ģ��)
* a��document���ĵ�����ģ�͵�һ����
* b��DOM��һ�����ϵ���������
>DOM���ǰ�HTML��Ϊһ����νṹ(���νṹ)���ĵ�

 * �ĵ�(Document)������ָHTML����XML�ļ�
 * �ڵ�(Node)��HTML�ĵ��е��������ݶ����Գ�֮Ϊ�ڵ�
 * Ԫ��(Element)��HTML�ĵ��еı�ǩ���Գ�ΪԪ�� 
 
###2.3 DOM�ڵ�Ļ�ȡ
�����ڵ�,���������ҵ���Ԫ��,�����ַ������������:

* a��ͨ��id�ҵ�HTMLԪ��
document.getElementById("demo");
* b��ͨ����ǩ���ҵ�HTMLԪ��
document.getElementsTagName("div");
* c��ͨ�������ҵ�HTMLԪ��
document.getElementByClassname("a");
* d��ͨ���������� HTML Ԫ���� IE 5,6,7,8 ����Ч
��ǩ=document.getElementById("demo"); ͨ��ID��ñ�ǩ
���ķ���ֵ��һ����ǩ������ֱ��ʹ�á��������ֵ���������ԡ�
��ǩ����= document.getElementsByTagName("div"); ͨ����ǩ����ñ�ǩ����
��ǩ����= document.getElementsByClassName("a");ͨ��������ñ�ǩ����
���������ķ���ֵ�Ǳ�ǩ���飬ϰ�����Ǳ���֮����ʹ�á�
��������������е�ֵֻ��1����     
document.getElementsByTagName("div")[0];ȡ�����е�һ��Ԫ��
document.getElementsByClassName("a")[0];ȡ�����е�һ��Ԫ��

##3. DOM���ʹ�ϵ(�ڵ�Ļ��)
�ڵ�ķ��ʹ�ϵ���������Եķ�ʽ���ڵģ�DOM�Ľڵ㲢���ǹ����ģ���˿���ͨ��DOM�ڵ�֮�����Թ�ϵ�����ǽ��з���
###3.1 ���ڵ㣨parentNode��
* a�����÷�ʽ���� �ڵ�.parentNode
�����߾��ǽڵ�,һ���ڵ�ֻ��һ�����ڵ�
* b����������
```javascript
var box2 = document.getElementById("box2")
console.log(box2.parentNode);
```

###3.2 �ֵܽڵ�
>sibling:�����ֵܵ���˼
next:��һ������˼
previous:ǰһ������˼

* a����һ���ֵܽڵ�=�ڵ�.nextElementSibling || �ڵ�.nextSibling
 * ��.nextSibling: �������ǽڵ���IE678��ָ��һ��Ԫ�ؽڵ�(��ǩ),�ڻ���ȸ�IE9+�Ժ�ָ������һ���ڵ�(�������ĵ��ͻ��нڵ�).
 * ��. nextElementSibling:�ڻ���ȸ�IE9��ָ������һ��Ԫ�ؽڵ�
�ܽ�:��IE678����nextSibing,�ڻ���ȸ�IE9+�Ժ���nextElementSibing
* b��ǰһ���ֵܽڵ�=�ڵ�.previousElemnentSibling || �ڵ�.previousSibling
 * ��. previousSibling:�������ǽڵ�,IE678��ָǰһ��Ԫ�ؽڵ�(��ǩ).�ڻ���ȸ�IE9+�Ժ�ָ����ǰһ���ڵ�(�������ĵ��ͻ��нڵ�)
 * ��. previousSibling:�ڻ���ȸ�IE9��ָ������һ��Ԫ�ؽڵ�
�ܽ�:��IE678����previousSibling,�ڻ���ȸ�IE9+�Ժ���previousElementSibling
 
###3.3 �����ӽڵ�
* a����һ���ӽڵ�=���ڵ�.firstElementChild || ���ڵ�.firstChild
 * ��.first:�������Ǹ��ڵ�,IE678��ָ��һ����Ԫ�ؽڵ�(��ǩ).�ڻ���ȸ�IE9+�Ժ�ָ���ǵ�һ���ڵ�(�����ĵ��ͻ��нڵ�)
 * ��. firstElementChild:�ڻ���ȸ�IE9��ָ�ĵ�һ��Ԫ�ؽڵ�
* b�����һ���ֵܽڵ�=���ڵ�.lastElementChild ||���ڵ�.lastChild
 * ��. lastChild:�������Ǹ��ڵ�,IE678��ָ���һ����Ԫ�ؽڵ�(��ǩ),�ڻ���ȸ�IE9+�Ժ�ָ�������һ���ڵ�(���޿��ĵ��ͻ��нڵ�)
 * ��. lastElementChild:�ڻ���ȸ�IE9+��ָ�������һ��Ԫ�ؽڵ�
 
###3.4 �����ӽڵ�
* a���ӽڵ�����=���ڵ�.childNodes  ��ȡ���нڵ�
ChildNodes:���Ǳ�׼����,������ָ��Ԫ�ص���Ԫ�ؼ���,����HTML�ڵ� �������� �ı��ڵ� (����W3C���׶���)
��� �ȸ�ȸ߰汾��ѻ���Ҳ�������ӽڵ�
 * ��.nodeType = 1  ��ʾ����Ԫ�ؽڵ�  ��ס Ԫ�ؾ��Ǳ�ǩ
 * ��. nodeType = 2 ��ʾ���Խڵ�
 * ��. nodeType = 3  ��ʾ�ı��ڵ�
* b���ӽڵ�����=���ڵ�.children;  �õ����
children:�Ǳ�׼����,������ָ��Ԫ�ص���Ԫ�ؼ���,
����ֻ����HTML�ڵ�,�����������ı��ڵ�,��Ȼ���Ǳ�׼��DOM����,������innerHTML����һ��,�õ��˼��������������֧��,
children ��IE678�а���ע�ͽڵ�,
��IETF78��,ע�ͽڵ㲻Ҫд������

###3.5 ֪ʶ����
* a���ڵ��Լ�.parentNode.children[index]; ����õ��ֵܽڵ�
* b����ȡ���е��ֵܽڵ�

```
function siblings(elm){
var a=[ ];
var p=elm.parentNode.children;
for(var i=0;i<p.length;i++){
if(p[i] !==elem){
a.push(p[i]);
}
}
return  a;
}
``` 
##4. DOM�ڵ����
###4.1 �����ڵ�
�µı�ǩ(�ڵ�)=document.creatElement("��ǩ��");
###4.2 ����ڵ�(ʹ�ýڵ�)
* a�����ڵ�.appendChild( );
���ڵ�.appendChild(�½ڵ�); ���ڵ��������һ���½ڵ�
* b�����ڵ�.insertBefore(Ҫ����Ľڵ�,�ο��ڵ�)
���ڵ�.insertBefore(�½ڵ�,�ο��ڵ�) �ڲο��ڵ�ǰ����
����ο��ڵ�Ϊnull,��ô�����ڽڵ�������һ���ڵ�

###4.3 ɾ���ڵ�
* a���÷�:�ø��ڵ�ɾ���ӽڵ�
���ڵ�.removeChild(�ӽڵ�); ����ָ��Ҫɾ�� ���ӽڵ�
�ڵ��Լ�ɾ���Լ�;
��֪�������������,������ôЩ:node.parentNode.removeChild(node)

###4.4 ���ƽڵ�
* a��oldNode.cloneNode(true)
�½ڵ�=Ҫ���ƵĽڵ�.cloneNode(����); ������ѡ���ƽڵ�
���ڸ��ƽڵ�,����һ����������,true��ʾ���(��ֵ�ڵ㼰�������ӽڵ�),false��ʾǳ����(���ƽڵ㱾��,�������ӽڵ�)

###4.5 ���ԡ���ֵ��ȡ���ַ�ʽ
* a��Ԫ�ؽڵ�.���Ի���Ԫ�ؽڵ�[����]
```
eleNode.src="image/jd2.png"
console.log(eleNode.src);
console.log(eleNode["title"]);
```
* b��Ԫ�ؽڵ�.����( );
 * ��.��ȡ: getAttribute(����)  ���Խڵ�
 * ��.����:setAttribute(����,ֵ)
 * ��.ɾ��:removeAttribute(����)
������:�ڵ�   �в��� û�з���ֵ ÿһ���������岻ͬ
```
ʾ������:
<body>
<div id="box" value="111">���</div>
<script>
var ele = document.getElementById("box");//Ԫ�ؽڵ�
var att = ele.getAttributeNode("id");//���Խڵ�
var txt = ele.firstChild;
console.log(ele);  //<div id="box" value="111">���</div>
console.log(att); //id="box"
console.log(txt); //"���"
```

###4.6 �ڵ�����
>value��innerHTML��innerText��textContent

* a��value:��ǩ��value����
* b��innerHTML:��ȡ˫�պϱ�ǩ���������(ʶ���ǩ)
* c��innerText:��ȡ˫�պϱ�ǩ���������(��ʶ���ǩ)(�ϰ汾�Ļ����textContent)
    * ��.�ϰ汾�Ļ����֧��innerText��֧��textContent
    * ��.p����Ƕ��p��h1����Ƕ��h1��a�����ڲ�����Ƕ��a����
 
##5. style������ʾ
>var box = document.getElementsByTagName("div")[0];

- 5.1 ��ʽ�ٵ�ʱ��ʹ��,
```
console.log(box.style.backgroundColor);
```
- 5.2 style�Ƕ���
```
console.log(box.style);
console.log(typeof box.style);
```
- 5.3 ֵ���ַ�����û������ֵ�ǡ�����
```
console.log(box.style.lineHeight);
console.log(box.style.border);
```
- 5.4 ���������շ���������css��һ��
```
console.log(box.style.backgroundColor);
```
- 5.5 ����������ʽ���ܻ�ȡ����ֻ������ʽ����������Ƕ�������޹أ�
```
console.log(typeof box.className);
```
- 5.6 box.style.cssText = ���ַ�����ʽ����ʽ����
```
console.log(box.style.cssText);
box.style.cssText = "width: 200px; height: 200px; background-color: red;line-height:200px;text-align:center;" 
```

##6. ��ʱ��
###6.1 ���ֶ�ʱ��
* a��setInterval( )
ѭ����ʱ��:�ܶ���ʼ��ִ��(ѭ��ִ��),�Ƚϳ���
* b��setTimeout( )
ը����ʱ��:�����Ժ����̱���(ִֻ��һ��)

##6.2 setInterval( )����ķ���
* a����ʽһ(��������)
```
setInterval(function () {
console.log(1);
},1000);
```

* b����ʽ��
```
setInterval(fn,1000);
function fn(){
console.log(2);
}
```
* c����ʽ��
```
setInterval("fn(3)",1000);
function fn(aaa){
console.log(aaa);
}
```

##6.3 �����ʱ��
```
//����ֵ�������ʱ����
var num = 1;
//setInterval���ķ���ֵ���Ƕ�ʱ��������
var timer = setInterval(function () {
console.log(num);
num++
if(num===10){
//���ֹͣ��ʱ���أ�����
clearInterval(timer);
}
},500);
```

##**7�����ö���String/Number/Boolean**
###**7.1�����������ַ�(charAt/charCodeAt)**
###7.1.1���ַ�/�ַ����� = Str.charAt/charCodeAt(����ֵ);
>��charAt����ȡ��Ӧλ���ַ��������� �ַ�λ�ã�
>>ע�ͣ��ַ����е�һ���ַ����±��� 0��������� index ���� 0 �� string.length ֮�䣬�÷���������һ�����ַ�����

>��charCodeAt��ȡ��Ӧλ���ַ����루������ �ַ�λ�ã���

###7.1.2��charAt()������charCodeAt()��������ѡȡ�ַ�����ĳһλ���ϵĵ����ַ�
>###����charCodeAt()����������������ָ��λ���ϵ��ַ��������Ƿ��ظ��ַ���Unicode�ַ����еı���ֵ�������λ��û���ַ�������ֵΪNaN.

###**7.2�����ַ���������indexOf/lastIndexOf��**
###7.2.1������ֵ = str.indexOf/lastIndexOf(��Ҫ��ѯ���ַ�);
>��indexOf����ǰ��������ַ���λ�ã������� �����ַ�����
>>��ǰ��Ѱ�ҵ�һ������Ԫ�ص�λ��

>��lastIndexOf���Ӻ���ǰ�����ַ���λ�ã������������ַ�����
>>�Ӻ���Ѱ�ҵ�һ������Ԫ�ص�λ��
�Ҳ����򷵻� -1

###**7.3��url ����ͽ��루�˽⣩**
###7.3.1��encodeURIComponent() �����ɰ��ַ�����Ϊ URI ������б���
###7.3.2��decodeURIComponent() �����ɰ��ַ�����Ϊ URI ������н���
>URI (Uniform ResourceIdentifiers,ͨ����Դ��ʶ��)���б��룬�Ա㷢�͸����������Ч��URI�в��ܰ���ĳЩ�ַ�������ո񡣶���URI���뷽���Ϳ��Զ�URI���б��룬�����������UTF-8�����滻������Ч���ַ����Ӷ���������ܹ����ܺ���⡣

###**7.4���ַ���������**
>���ַ��� = str1.concat(str2);���������ַ���

###**7.5���ַ����Ľ�ȡ**
###7.5.1��slice����ȡ�ַ�����������1����ȡλ�á����롿��2�ս�㣩
�ַ��� = str.slice������1������2); ����������������ֵ��

* ��2,5��  �������󲻰��ҡ�
*  ( 2 )   	��ָ��������λ�ü������
* ��-3��   �ӵ����ڼ����������.
* ��5,2��  ǰ��Ĵ󣬺����С���ա�

###7.5.2�� substr����ȡ�ַ�����������1����ȡλ�á����롿��2��ȡ���ȣ�
�ַ��� = str.substr������1������2); 1����ֵ,2���ȡ�
��һ������Ϊ������λ��ȡֵ���ڶ������������ַ����ȡ�

* ��2,4��    ������ֵΪ2���ַ���ʼ����ȡ4���ַ���
* ��1��     һ��ֵ����ָ��λ�õ����
* ��-3��    �ӵ����ڼ����������.
*  ������ǰ���С�������

###7.5.3�� slice����ȡ�ַ�����������1����ȡλ�á����롿��2�ս�㣩
�ַ��� = str.slice������1������2); ����������������ֵ��
��ͬ1���������ܵ�תλ�á�
��ͬ2��������ֵ����ȫ����ȡ�ַ�����

* (2,5)    �������󲻰��ҡ�
* ( 2 )      ��ָ��������λ�ü������
* (-3)    ��ȡȫ���ַ���.
* (5,2)   ǰ��Ĵ󣬺����С�����ǿա���2,5��

###**7.6�����ⷽ�����**
* trim()     //ֻ��ȥ���ַ���ǰ��Ŀհ�
* replace()  //�滻   str.replace(/aaa/gi,��bbb��);g ͨ�õ���˼ str�����ȫ���滻  //i �����ִ�Сд
* split()    //�ַ���������
* ��Сдת������
    * ��str.toLowerCase()  //ת����д
    * ��str.toUpperCase() //ת��Сд

##**8��Math**
* Math.abs();       ȡ����ֵ
* Math.floor();      ����ȡ�� ��Сȡ
* Math.ceil();       ����ȡ�� ���ȡ
* Math.round();     ��������ȡ�� ������������ ������������
* Math.random();   �����0-1

##**9���¼�����**
###**9.1���¼�����ԭ��**
```
//ԭ���˽⣩���Լ���װһ����(click)
    function fn(str,fn,ele){
        //�ж�λ��Ҫע�⣺���������¼�������ô���¼��Ѿ�������
        //���Ի�ȡ�ɵ��¼��������µ��¼���֮ǰ
        var oldEvent = ele["on"+str];
        ele["on"+str] = function () {
            //����ֱ��ִ�к�������Ϊ���ǻ���֪����ǰ��û�а���ͬ�����¼�
            //�����жϣ������ǰ�й����¼�����ô����ǰ��ִ�������ִ�����ڵ��¼������û�о�ֱ��ִ��
            //���û�б�������¼����¼�Դ�ĸ��¼�����Ӧ����null��Ӧ��booleanֵ��false
            //����Ѿ�������¼����¼�Դ�ĸ��¼�����Ӧ����function�����Ӧ��booleanֵ��true
            if(oldEvent){
                //��ΪoldEvent���������Ǻ���������ô�����һ��();����ִ�к���
                oldEvent();
                fn();
            }else{
                //û�а󶨹��¼�
                fn();
            }
        }
    }
```
###**9.2���¼���ӵļ��ݣ�**
###9.2.1������ȸ�IE9+֧��addEventListener
btn.addEventListener("click",fn1);
###9.2.2��IE678֧��attachEvent
btn.attachEvent("onclick",fn1);
###9.2.3���¼���Ӽ���д��
```
 EventListen = {
        addEvent: function (ele,fn,str) {
            //ͨ���жϵ��õķ�ʽ����IE678
            //�ж�������Ƿ�֧�ָ÷��������֧����ô���ã������֧�ֻ���������
            if(ele.addEventListener){
                //ֱ�ӵ���
                ele.addEventListener(str,fn);
            }else if(ele.attachEvent){
                ele.attachEvent("on"+str,fn);
            }else{
                //��addEventListener��attachEvent�������ڵ�����£��ô˴���
                ele["on"+str] = fn;
            }
        }
    }
```
###**9.3���¼��Ƴ��ļ��ݣ�**
###9.3.1������ȸ�IE9+֧��removeEventListener
btn.removeEventListener("click",fn1);
###9.3.2��IE678֧��detachEvent
btn.detachEvent("onclick",fn1);
###9.3.3���¼��Ƴ�����д��
```
removeEvent: function (ele,fn,str) {
            if(ele.removeEventListener){
                ele.removeEventListener(str,fn);
            }else if(ele.detachEvent){
                ele.detachEvent("on"+str,fn);
            }else{
                ele["on"+str] = null;
            }
        }
```
###**9.4��addEventListener��attachEvent������**
###9.4.1 �¼����Ƶ�����
addEventLisener�е�һ������type��click��load������on
attachEvent��һ������type��onclick��onload
###9.4.2 this������
addEventLisener���¼����������ڵ�ǰ��������������У���ˣ�ʱ�䴦������this���ǵ�ǰ����
attachEvent���¼������������ȫ�����������������this����window












