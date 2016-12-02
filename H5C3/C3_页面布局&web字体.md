# C3_ҳ�沼��&web����
## 1. ҳ�沼��
### 1.1 ��������
- ���������
CSS3�ڲ��ַ������˷ǳ���ĸĽ���ʹ�����ǶԿ鼶Ԫ�صĲ������б��ʮ������Ӧ�Էǳ�ǿ����ǿ��������ԣ�����Ӧʽ���п��Է��Ӽ�������á�
    + ���᣺Flex������������Ҫ��������Flex��Ŀ��Ĭ����ˮƽ����
    + ���᣺�����ᴹֱ����������ᣬĬ���Ǵ�ֱ�����
    + ����Ĭ������������ң�����Ĭ�ϴ��ϵ���
    + ����Ͳ��Ტ���ǹ̶�����ģ�ͨ��flex-direction���Ի�����
- ��ҪԪ�أ�
    + ָ��һ������Ϊ�������� display: flex
    + ���������������˺е���Ԫ�صĲ��ַ�ʽ ���� flex-direction
    + ��ȷ�����ἰ����
    + �ɻ��������ᣬҲ�ɸı䷽��
- ���������
    + flex-direction�������᷽��Ĭ��Ϊˮƽ����
    ������ͨ������flex���������᷽��������felx������flex�����е�λ��
        * flex-direction:row  ˮƽ����
        * flex-direction:reverse-row   ˮƽ��ת
        * flex-direction:column  ��ֱ
        * flex-direction:column-reverse  ��ֱ��ת
    + justify-content��������(����)����
        * justify-content ���û�������Ժ���Ԫ��������(����)�����ϵĶ��뷽ʽ
        * justify-content:flex-start �����Ὺʼ�ķ������ (������)
        * justify-conten:flex-end;����������ķ������(�յ����)
        * justify-content:center; ���ж���
        * justify-content:space-around; �ڸ�������ƽ��
        * justify-content:space-between; ���˶��� ƽ��
    + align-items��������(����)����
        * align-items���û�������Ժ���Ԫ�������ᣨ���ᣩ�����ϵĶ��뷽ʽ��
        * align-items:flex-start  �Ӳ��Ὺʼ�ķ��ж���(������)
        * align-items:flex-end;�Ӳ������������(�յ����)
        * align-items:center; ����
        * align-items:baseline; ���߶��� Ĭ��ͬflex-start
        * align-items:stretch; ����
    + flex����Ŀ����������ű�������ָ��flex���ԣ��򲻲�����������
    + ���������˽�
    + flex-wrap�����Ƿ���
    + align-content��ջ����flex-wrap�����Ķ����У�����
    + flex-flow��flex-direction��flex-wrap�ļ�д��ʽ
    + order��������Ŀ������˳������ʽ���򣬴�С����

### 1.2 ���в���
- ���ĵ��ֳ�3��
-webkit-column-count: 3;
- ���÷������
-webkit-column-gap: 50px;
- ���÷ָ��ߵ���ɫ
-webkit-column-rule: 1px dashed red;
- ���÷����Ŀ��
-webkit-column-width:200px;

## 2. Web����
### 2.1 �������
������Ա����Ϊ���ѵ���ҳָ����������壬���迼���û��������Ƿ�װ�˴��������壬�Ӵ˰��������崦���ͼƬ��ʱ�����Ϊ�˹�ȥ��
֧�̶ֳȱȽϺã�����IE�Ͱ汾�����Ҳ��֧�֡�

- ʹ�ò��裺
    1. ���������
    2. �������壺���������ȥ��������
    3. ��������
    4. �ڽṹ��д ͼ��ı��룬����ǩ�������

### 2.2	�����ʽ
��ͬ�������֧�ֵ������ʽ�ǲ�һ���ģ������б�Ҫ�˽�һ���й������ʽ��֪ʶ��

1. TureTpe(.ttf)��ʽ
.ttf������Windows��Mac����������壬��һ��RAW��ʽ��֧������������������IE9+��Firefox3.5+��Chrome4+��Safari3+��Opera10+��iOS Mobile��Safari4.2+��
2. OpenType(.otf)��ʽ
.otf���屻��Ϊ��һ��ԭʼ�������ʽ����������TureType�Ļ����ϣ�֧������������������Firefox3.5+��Chrome4.0+��Safari3.1+��Opera10.0+��iOS Mobile��Safari4.2+��
3. Web Open Font Format(.woff)��ʽ
woff������Web��������Ѹ�ʽ������һ�����ŵ�TrueType/OpenType��ѹ���汾��ͬʱҲ֧��Ԫ���ݰ��ķ��룬֧������������������IE9+��Firefox3.5+��Chrome6+��Safari3.6+��Opera11.1+��
4. Embedded Open Type(.eot)��ʽ
.eot������IEר�����壬���Դ�TrueType�����˸�ʽ���壬֧������������������IE4+��
5. SVG(.svg)��ʽ
.svg�����ǻ���SVG������Ⱦ��һ�ָ�ʽ��֧������������������Chrome4+��Safari3.1+��Opera10.0+��iOS Mobile Safari3.2+��
�˽��������֪ʶ�����Ǿ���ҪΪ��ͬ�������׼����ͬ��ʽ�����壬ͨ�����ǻ�ͨ���������ɹ��߰��������ɸ��ָ�ʽ�����壬�������������������ʽ���������졣 
�����������վ.
�Ƽ�http://www.zhaozi.cn/��http://www.youziku.com/ ���Ҹ�����������
6. ʹ�÷���
```
 @font-face {font-family: 'webfont';
    src: url('font/webfont.eot'); /* IE9*/
    src: url('font/webfont.eot?#iefix') format('embedded-opentype'), /* IE6-IE8 */
    url('font/webfont.woff') format('woff'), /* chrome��firefox */
    url('font/webfont.ttf') format('truetype'), /* chrome��firefox��opera��Safari, Android, iOS 4.2+*/
    url('font/webfont.svg#webfont') format('svg'); /* iOS 4.1- */
}
/* ����һ��������˭�����������ͻ�ʹ��webfont����*/
.webfont{
    font-family: 'webfont';
}
```

### 2.3	����ͼ��
��ʵ���ǿ��԰�����������һ��������״��ͼƬ��Ҳ���԰�ͼƬ��������
�������ǰ���ҳ���õ�һЩС��ͼ�꣬�������߰���������һ���������Ȼ��Ϳ�����ʹ������һ��ʹ��ͼ���ˡ�
- �ŵ㣺
    + ������ͼ����������⣬��������
    + ����ʸ���ԣ��ɱ�֤�����ȣ�
    + ʹ��������ά����
- Font Awesome ʹ�ý���
    http://fontawesome.dashgame.com/
- �������ѵ�����ͼ���
    + http://iconfont.cn/
    + https://icomoon.io/
- SVG�ز�  http://www.iconsvg.com/
- ʹ�÷���
```
@font-face {font-family: 'my-icon';
    src: url('font/iconfont.eot'); /* IE9*/
    src: url('font/iconfont.eot?#iefix') format('embedded-opentype'), /* IE6-IE8 */
    url('font/iconfont.woff') format('woff'), /* chrome��firefox */
    url('font/iconfont.ttf') format('truetype'), /* chrome��firefox��opera��Safari, Android, iOS 4.2+*/
    url('font/iconfont.svg#iconfont') format('svg'); /* iOS 4.1- */
}
.my-font{
font-family: "my-icon";
}
```

## 3. �������¼�
```
  var num=0;
//    �������¼�
    window.onmousewheel=function(){
        num++;
        console.log(num);
    }
```

    