# **�������_offset����**
## 1.1 ��������һ���¼�����
- offset ����
- scroll����
- client����
- event�¼�����

## 1.2 Offset������
> offsetWidth��offsetHight�Լ�offsetLeft��offsetTop�Լ�offsetParent��ͬ�����offset���塣

### 1.2.1 offsetWidth��offsetHight��������������+padding+border��
> ���������ԣ����ǰ��������еĽڵ�Ԫ���ϡ���ȡ֮��ֻҪ�������������ԣ����Ǿ��ܹ���ȡԪ�ؽڵ�Ŀ�͸ߡ�

- offset��/��  =  ��������Ŀ�/�� + padding +border��������margin
- offsetWidth = width+padding+border��
- offsetHeight = Height+padding+border

### 1.2.2 offsetLeft��offsetTop�������븸�����ж�λ����/����ľ��룩
> ���ؾ����ϼ����ӣ����ж�λ����ߵ�λ�����������û�ж�λ����bodyΪ׼
offsetLeft �Ӹ��׵�padding ��ʼ��,���׵�border ���㡣
�ڸ������ж�λ������£�offsetLeft == style.left(ȥ��px)

###1.2.3 offsetParent����⸸ϵ�����д��ж�λ�ĸ����ӽڵ㣩
- 1�����ظĶ���ĸ��� �����ж�λ��
	>�����ǰԪ�صĸ���Ԫ��û�н���CSS��λ��positionΪabsolute��relative��fixed����offsetParentΪbody��

- 2�������ǰԪ�صĸ���Ԫ������CSS��λ	
    > ��positionΪabsolute��relative��fixed����offsetParentȡ������Ǹ�����Ԫ�ء�

## 1.3 offsetLeft��style.left����
> 
1. �����������offsetLeft���Է���û�ж�λ���ӵľ�������λ�á�
    - �����ϵ�����ж�û�ж�λ����bodyΪ׼��
    - style.leftֻ�ܻ�ȡ����ʽ�����û�з��ء���;
2. offsetTop ���ص������֣���style.top���ص����ַ��������������⻹���е�λ��px��
    - div.offsetLeft = 100;    div.style.left = "100px";
3. offsetTop ֻ������ style.top�ɶ�д����ֻ���ǻ�ȡֵ����д�Ǹ�ֵ��
    - style.left��style.top���Ը�ֵ
    - offsetLeft��offsetTopֻ�ܻ�ȡֵ
4. ���û�и� HTML Ԫ��ָ���� top ��ʽ����style.top���ص��ǿ��ַ�����
    - style.leftֻ�ܻ�ȡ����ʽ�����û�з��ء���;

**style.left��=����ߺ��ұ߻���һ��������ߵ�ʱ�������ԣ��ұߵ�ʱ����ֵ��**







