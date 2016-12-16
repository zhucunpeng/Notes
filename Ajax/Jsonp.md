## Jsonp原理： 
- 首先在客户端注册一个callback,然后把callback的名字传给服务器。
- 此时，服务器先生成 json 数据。然后以 javascript 语法的方式，生成一个function , function名字就是传递上来的参数 jsonp.

- 最后将 json 数据直接以入参的方式，放置到 function 中，这样就生成了一段 js 语法的文档，返回给客户端。

- 客户端浏览器，解析script标签，并执行返回的 javascript 文档，此时数据作为参数，传入到了客户端预先定义好的 callback 函数里.（动态执行回调函数）

- 使用JSON的优点在于：
    + 比XML轻了很多，没有那么多冗余的东西。
    + JSON也是具有很好的可读性的，但是通常返回的都是压缩过后的。不像XML这样的浏览器可以直接显示，浏览器对于JSON的格式化的显示就需要借助一些插件了。
    + 在JavaScript中处理JSON很简单。
    + 其他语言例如PHP对于JSON的支持也不错。
- JSON也有一些劣势：
    + JSON在服务端语言的支持不像XML那么广泛，不过JSON.org上提供很多语言的库。
    + 如果你使用eval()来解析的话，会容易出现安全问题。
尽管如此，JSON的优点还是很明显的。他是Ajax数据交互的很理想的数据格式。

### 客户端jQuery.ajax的调用代码示例
```
 $.ajax( {
	type:'get', //jquey是不支持post方式跨域的  
	async:false, url:" ", //跨域请求的URL  
	dataType:'jsonp', //传递给请求处理程序，用以获得jsonp回调函数名的参数名(默认为:callback) 
	sonp:'jsoncallback', //自定义的jsonp回调函数名称，默认为jQuery自动生成的随机函数名 
	jsonpCallback:"success_jsonpCallback", //成功获取跨域服务器上的json数据后,会动态执行这个callback函数 
	success:function(result) {
		alert(result.img_url);
	}
});
```

### 服务器端示例代码，php代码: 
```
$data['status'] = "1"; 
$data['img_url'] = "";  
$jsoncallback = $_GET['jsoncallback']; 
echo $jsoncallback."(".json_encode($data).")"
```

### 在异域服务器的showAll函数里，

```
var db=require("./database");
exports.showAll=function(req, res) {
	/**设置响应头允许ajax跨域访问**/
	res.setHeader("Access-Control-Allow-Origin", "*");
	/*星号表示所有的异域请求都可以接受，*/
	res.setHeader("Access-Control-Allow-Methods", "GET,POST");
	var con=db.getCon();
	con.query("select * from t_students", function(error, rows) {
		if(error) {
			console.log("数据库出错："+error);
		}
		else {
			/*注意这里，返回的就是jsonP的回调函数名+数据了*/
			res.send("cb("+JSON.stringify(r)+")");
		}
	}
	);
}
```