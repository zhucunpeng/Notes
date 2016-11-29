#内置对象(数组)
##1. 数组高级API和Array的内置方法
###1.1 学习API的方法
* 侧重点
调用者: 谁调用的              参数:有无,几个
返回值:有无  什么类型      功能:干什么的 
* 自学方法
 * 离线  
     * 离线文档
 * 在线 
     * W3C 前端标准(W3CSchool)
     * MDN (开发者网站) https://developer.mozilla.org/zh-CN/
     
###1.2 判断数组
* instanceof: 是一个关键字    判断A是否是B类型
布尔类型值=A instanceof B
* Array.isArray( ) //HTML5中新增  判断是不是数组
布尔类型值=Array.isArray(变量)
调用者:Array   参数:变量(被检测值)  返回值:布尔类型

###1.3 转换数组
* toString()  把数组转换成字符串 每一项用,分割
字符串=数组.toString();
* valueOf()   返回数组对象本身
数组本身=数组.valueOf( );
* join: 根据每个字符把数组元素连接起来变成字符串
字符串=数组.join(变量)
变量可以有可以没有,不写默认用逗号分隔,无缝连接用空字符串

###1.4 数组增删和换位置(原数组将被修改)
* push()  在数组最后面插入项,返回数组的长度
数组1改后的长度=数组1.push(元素1);
* pop()   取出数组中的最后一项,返回最后一项
被删除的元素=数组1.pop();
* unshift( ) 在数组最前面插入项,返回数组的长度
数组1改后的长度=数组1.unshift(元素1);
* shift( ) 取出数组中的第一个元素,返回第一项
被删除的元素=数组1.shift( );
* reverse( ) 翻转数组(原数组将被翻转,返回值也是被翻转后的数组)
翻转后的数组=数组1.reverse( );
* sort( )  给数组排序,返回排序后的数组 如何排序看参数
从小到大排序后的数组=数组1.sort(function(a,b){
return a-b; 升序
});
无参:按照数组元素的首字符对应的unicode编码值从小到大排列数组元素
带参:必须为函数(回调函数-callback),函数中带有两个参数,代表数组中的前后元素,如果计算后(a-b),返回值为负数,a排b前面，降序;等于0不动;返回值为正数,a排b后面，升序
 
###3.5 数组的拼接 删除和替换
* a、concat()  把参数拼接到当前数组
新数组=数组1.concat(数组2);
* b、slice()   从当前数组中截取一个新的数组,不影响原来的数组,参数start从0开始end从1开始
新数组=数组1.slice(索引1,索引2); 索引值包括左边的不包括右边的
* c、splic( )  删除或替换当前数组的某些项目,参数start,deleteCount,options (要替换的项目)
新数组= 数组1.splice(起始索引，结束索引，替换内容);
* d、indexOf( )  从前往后给元素查索引,找到一个后,立刻返回;
      lastIndexOf( )从后往前给元素查索引,找到一个后,立刻返回
索引值= 数组.indexOf()/lastIndexOf(数组中的元素);
* f.  迭代方法 不会修改原数组
every()、filter()、forEach()、map()、some()
```
数组/boolean/无 = 数组.every/filter/forEach/map/some(
  function(element,index,arr){
     程序和返回值；                       
   }
);
```
>对数组中每一项运行以下函数，如果都返回true，every返回true，如果有一项返回false，则停止遍历 every返回false；不写默认返回false
array.every(function(item,index,arr) {
})
//对数组中每一项运行以下函数，该函数返回结果是true的项组成的新数组
var arr = array.filter(function(item,index,arr) {
});
console.log(arr); 
//遍历数组
array.forEach(function(item,index,arr){
});
//对数组中每一项运行以下函数，返回该函数的结果组成的新数组
var arr = array.map(function(item,index,arr) {
    return "\"" + item + "\"";
})
//对数组中每一项运行以下函数，如果该函数对某一项返回true，则some返回true
var b =  array.some(function(item,index,arr) {
    if (item == "ww") {
        return true;
    }
    return false;
});

###3.6 清空数组
* a、array.splice(0,array.length);  删除数组中所有项目
* b、array.length=0;  length属性可以赋值,其他语言中length是只读
* c、array=[ ];  推荐
* d、伪数组不能使用

###3.7 伪数组和arguments

* Array.from(伪数组);伪数组变成真数组

```
Array.from("foo"); // ["f", "o", "o"]
```

```
fn(1,2);  //传进去的实参个数可以大于形参的个数
function fn(a,b){
//只在函数中使用，实参的数组。
arguments[0] = 0;
console.log(arguments);
// 伪数组：不能修改长短的数组。(可以修改元素，但是不能变长变短)
// arguments.push(1);
console.log(arguments instanceof Array);
//形参个数
console.log(fn.length);
//实参个数
console.log(arguments.length);
// arguments.callee整个函数。函数名。
console.log(arguments.callee);
}
```