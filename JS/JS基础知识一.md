 
#Javascript基础知识一
##1、JS基础介绍
###1.1 概念
>Js是一门运行在客户端的编程语言。

###1.2 组成
* ?Ecmascript  js语法标准
* ?Dom        通过js操作网页元素
* ?Bom      通过api操作浏览器

###1.3 特点
* ?简单易用
* ?解释执行（js解释型的语言）
Js代码不通过编译，直接通过js引擎执行代码。
* ?基于对象

###1.4 JS书写位置
* ?内嵌式写法
```
 <script type=”text/javascript”>
    Js代码
 </script>
```
* ?外连式写法
```
 <script   type=”text/javascript” src=”1.js”>
        该标签内不能再写js代码
 </script>
```

### 1.5 Js 在页面中输入消息的几种方式
* ?alert(“”);  页面弹出对话框
* ?confirm(“”);在页面弹出一个对话框，有确定和取消按钮
* ?prompt(“”);         弹出对话框，拥抱与接收用户输入的信息
* ?console.log(“”);      在网页控制台中输出消息
* ?document.write(“”);  直接在页面中输出消息，可以写上html标签。
    * 转义字符
    *  \" 转双引
    *  \' 转单行
    *  \n 转换行
    *  \r 转回车
* ?JS注释;  快捷键ctrl+/，单行注释//   多行注释/*     */

##2、变量
###2.1 定义阐述：
* ?变量就是用来存储数据的容器
* ? 通过var 关键字定义一个变量
   var  n1;   //定义变量
* ?变量的赋值
  通过赋值运算符“=” 给变量赋值。
   var  n2=123;     //定义变量并赋值为123
* 注意：
  如果想要比较两个变量是否相同，不能使用“=”进行比较。
  
###2.2 变量的命名规范：
* 不能使用纯数字或数字开头定义变量
* 不能使用纯特殊字符或者开头（“_”除外）定义变量
* 不推荐使用汉字定义变量
* 不能使用关键字定义变量
* 不推荐使用保留字定义变量

* js中区分字母大小写。 

##3、数据类型
###3.1 简单数据类型
* number   数字类型
    * 十进制表示法
    * 十六进制表示法：从0-9，a(A)-f(F)表示数字，以0X开头
    * 八进制表示法：以0开头 0-7组成
* string  字符串类型
    * 凡是用双引号或者单引号引起的都是字符串
    * var   s1=”123”;   s1的数据类型字符串
* Boolean   布尔类型
只有两个值，一个是true 一个是false 实际运算中 true=1,false=0
 * true      真 （正确的）
 * false     假（错误的）
 * undefined     变量未初始化
     * var s1; 定义了变量，但是没有给变量赋值，那么该值的数据类型就是
* undefined 类型
     * 变量取值为null的时候   值为空 object
var   s1=null;  表示变量值为空，该变量在内存中是不存在的。真正的空。   s1的数据类型为 object

##3.2 复杂数据类型;
* object    对象
* Array       数组

##3.3 判断数据类型;
>通过typeof(变量) 进行数据类型的判断
Var   s1=123;
 alert(typeof(s1));     //number类型
 
##4、算术运算符
###4.1   +  加号

* 两个数字类型的变量相加，得到的是一个数字类型
* 一个数字类型和一个字符串相加，得到的是一个字符串

###4.2  -减号
* 两个数字类型的变量相减，得到的是一个数字类型
* 一个数字类型和一个数字字符串相减，得到的是一个数字类型。
*  一个数字类型和一个非数字字符串相减，得到的是NaN,是一个数字类型

###4.3  / 除号
* 两个数字类型的变量相除，得到的是一个数字类型。
* 一个数字类型和一个数字字符串相除，得到的是一个数字类型
* 一个数字类型和一个非数字字符串相除，得到的是NaN,是一个数字类型。
* 0做为除数的时候，得到结果 Infinity （无限大），是一个数字类型。

###4.4  %获取余数

###4.5  ( )优先级 有括号先计算括号里面的值





 
 
 