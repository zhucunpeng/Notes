#���ö���(����)
##1. ����߼�API��Array�����÷���
###1.1 ѧϰAPI�ķ���
* ���ص�
������: ˭���õ�              ����:����,����
����ֵ:����  ʲô����      ����:��ʲô�� 
* ��ѧ����
 * ����  
     * �����ĵ�
 * ���� 
     * W3C ǰ�˱�׼(W3CSchool)
     * MDN (��������վ) https://developer.mozilla.org/zh-CN/
     
###1.2 �ж�����
* instanceof: ��һ���ؼ���    �ж�A�Ƿ���B����
��������ֵ=A instanceof B
* Array.isArray( ) //HTML5������  �ж��ǲ�������
��������ֵ=Array.isArray(����)
������:Array   ����:����(�����ֵ)  ����ֵ:��������

###1.3 ת������
* toString()  ������ת�����ַ��� ÿһ����,�ָ�
�ַ���=����.toString();
* valueOf()   �������������
���鱾��=����.valueOf( );
* join: ����ÿ���ַ�������Ԫ��������������ַ���
�ַ���=����.join(����)
���������п���û��,��дĬ���ö��ŷָ�,�޷������ÿ��ַ���

###1.4 ������ɾ�ͻ�λ��(ԭ���齫���޸�)
* push()  ����������������,��������ĳ���
����1�ĺ�ĳ���=����1.push(Ԫ��1);
* pop()   ȡ�������е����һ��,�������һ��
��ɾ����Ԫ��=����1.pop();
* unshift( ) ��������ǰ�������,��������ĳ���
����1�ĺ�ĳ���=����1.unshift(Ԫ��1);
* shift( ) ȡ�������еĵ�һ��Ԫ��,���ص�һ��
��ɾ����Ԫ��=����1.shift( );
* reverse( ) ��ת����(ԭ���齫����ת,����ֵҲ�Ǳ���ת�������)
��ת�������=����1.reverse( );
* sort( )  ����������,�������������� ������򿴲���
��С��������������=����1.sort(function(a,b){
return a-b; ����
});
�޲�:��������Ԫ�ص����ַ���Ӧ��unicode����ֵ��С������������Ԫ��
����:����Ϊ����(�ص�����-callback),�����д�����������,���������е�ǰ��Ԫ��,��������(a-b),����ֵΪ����,a��bǰ�棬����;����0����;����ֵΪ����,a��b���棬����
 
###3.5 �����ƴ�� ɾ�����滻
* a��concat()  �Ѳ���ƴ�ӵ���ǰ����
������=����1.concat(����2);
* b��slice()   �ӵ�ǰ�����н�ȡһ���µ�����,��Ӱ��ԭ��������,����start��0��ʼend��1��ʼ
������=����1.slice(����1,����2); ����ֵ������ߵĲ������ұߵ�
* c��splic( )  ɾ�����滻��ǰ�����ĳЩ��Ŀ,����start,deleteCount,options (Ҫ�滻����Ŀ)
������= ����1.splice(��ʼ�����������������滻����);
* d��indexOf( )  ��ǰ�����Ԫ�ز�����,�ҵ�һ����,���̷���;
      lastIndexOf( )�Ӻ���ǰ��Ԫ�ز�����,�ҵ�һ����,���̷���
����ֵ= ����.indexOf()/lastIndexOf(�����е�Ԫ��);
* f.  �������� �����޸�ԭ����
every()��filter()��forEach()��map()��some()
```
����/boolean/�� = ����.every/filter/forEach/map/some(
  function(element,index,arr){
     ����ͷ���ֵ��                       
   }
);
```
>��������ÿһ���������º��������������true��every����true�������һ���false����ֹͣ���� every����false����дĬ�Ϸ���false
array.every(function(item,index,arr) {
})
//��������ÿһ���������º������ú������ؽ����true������ɵ�������
var arr = array.filter(function(item,index,arr) {
});
console.log(arr); 
//��������
array.forEach(function(item,index,arr){
});
//��������ÿһ���������º��������ظú����Ľ����ɵ�������
var arr = array.map(function(item,index,arr) {
    return "\"" + item + "\"";
})
//��������ÿһ���������º���������ú�����ĳһ���true����some����true
var b =  array.some(function(item,index,arr) {
    if (item == "ww") {
        return true;
    }
    return false;
});

###3.6 �������
* a��array.splice(0,array.length);  ɾ��������������Ŀ
* b��array.length=0;  length���Կ��Ը�ֵ,����������length��ֻ��
* c��array=[ ];  �Ƽ�
* d��α���鲻��ʹ��

###3.7 α�����arguments

* Array.from(α����);α������������

```
Array.from("foo"); // ["f", "o", "o"]
```

```
fn(1,2);  //����ȥ��ʵ�θ������Դ����βεĸ���
function fn(a,b){
//ֻ�ں�����ʹ�ã�ʵ�ε����顣
arguments[0] = 0;
console.log(arguments);
// α���飺�����޸ĳ��̵����顣(�����޸�Ԫ�أ����ǲ��ܱ䳤���)
// arguments.push(1);
console.log(arguments instanceof Array);
//�βθ���
console.log(fn.length);
//ʵ�θ���
console.log(arguments.length);
// arguments.callee������������������
console.log(arguments.callee);
}
```