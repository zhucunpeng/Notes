## MVC
- 是一种开发模式，由模型(Module)、视图(View)、控制器(Controler)
- 模型(Model) 一般用来处理数据(读取/设置)，一般指操作数据库
- 视图(View) 一般用来展示数据，比如通过HTML
- 控制器(controller) 一般用作链接模型和视图的桥梁

## 模块化
### 定义应用 通过为任一HTML标签添加ng-app属性，
- 为html标签添加ng-app表明整个文档都是应用，ng-app可以不赋值，但是要关联响应模块时则必须赋值
` <html ng-app = "App"> `

### 定义模块
- AngularJs提供了一个全局对象angular，其中angular.module()方法来定义一个模块
`var app = angular.module('app',[])`
- 通过module方法定义模块
- 需要传递两个参数，第一个表示模块的名称，第二个表示此模块依赖其他模块

### 定义控制器
- 控制器作为链接模型和视图的桥梁存在
```
app.controller('Demo',['$scope',function($scope){
    $scope=[
        {name:'刘德华',sex:'男',age:20}
        {name:'刘德华',sex:'男',age:20}
    ]
}])
```
- app是一个模块实例对象，通过这个实例对象定义控制器，需要两个参数，第一个参数表示控制器名称，第二个参数是一个数组，这个数组除最后一个单元室函数外，其余都是字符串，标明此控制器的依赖关系
- 模型数据是要展示到视图上的，所以需要将控制器关联到视图上，通过为HTML标签添加ng-controller属性并赋值相应的控制器的名称，就确立了关联关系
```
<tbody ng-controller="StarsController">
	<tr ng-repeat="star in stars">
		<td>{{star.name}}</td>
		<td>{{star.sex}}</td>
		<td>{{star.age}}</td>
	</tr>
</tbody>
```

## 指令
### 内置指令
- ng-app 指定应用根元素，至少有一个元素制订了此属性
- ng-controller 指定控制器
- ng-show控制元素是否显示 true显示 false不显示
- ng-hide控制元素是否隐藏，true隐藏 false不隐藏
- ng-if 控制元素是否存在，true存在，false 不存在
- ng-src增强图片路径
- ng-href增强地址
- ng-class控制类名
- ng-include引入模板
- ng-disabled表单禁用
- ng-readonly 表单只读
- ng-checked单/复选框表单选中
- ng-selected下拉框表单选中

### 自定义指令
- 根据实际业务需要自定义指令，通过angular全局对象下的directive方法实现
```
var App = angular.module('App', []);
// 通过模块实例对象的directive方法可以自定义指令
App.directive('tag', function () {
	// 返回一个对象，这个对象就是自定义指令相关的内容
	return {
		// E element
		// A attribute
		// C class
		// M mark replace 必须为true
		restrict: 'ECMA',
		// template: '<ul><li>首页</li><li>列表</li></ul>',
		templateUrl: './list.html',
		// replace: true
	}
});
```

## 数据绑定
数据绑定指的就是将模型中的数据与相应的视图进行关联，分为单向绑定和双向绑定
### 单向绑定
- 单向书库绑定是指将模型数据，按着下好的视图模板生成HTML标签，然后追加到DOM中显示，

### 双向绑定
- 则可以实现模型数据和视图模板的双向传递

### 相关指令
- 通过{{}}和ng-bind指令来实现模型数据项视图模板的绑定，其区别在于{{}}绑定数据时会有闪烁现象，添加ng-cloak也可以解决闪烁现象，通过ng-bind-template可以绑定多个数据
```
<ul ng-controller="DemoController">
    <li ng-bind="name"></li>
    <li ng-cloak>{{name}}{{age}}</li>
    <li ng-bind-template="{{name}}{{age}}"></li>
</ul>
```
- 通过为表单添加ng-module指令实现视图模板向模型数据的绑定
- 通过ng-init可以初始化模型(module)也就是$scope
- Angular对事件进行了扩展在原有事件名称基础上添加ng-作为前缀
- ng-repeat可以将数组或对象数据迭代到视图模板中ng-switch,on,ng-switch-when可以对数据进行筛选
```
<li ng-repeat="item in items" ng-switch="item">
	<span ng-switch-when="css">{{item}}</span>
</li>
```

## 作用域
### 根作用域
- 一个angular的应用App在期待能够的时候会自动创建一个根作用域$rootscope,这个根作用域在整个应用范围(ng-app所在标签内)都是可以被访问的
- 指定一个普通的div为应用的根源元素，这个根元素对应的便是$rootscope，通过ng-init为$rootscope添加数据
```
<div ng-app="App" ng-init="name='jack';age=18">
    <span>{{age}}{{span}}</span>
<div>
```

### 子作用域
- 通过ng-controller指令可以创建一个子作用域，新建的作用域可以访问其父作用域的数据。

## 过滤器
### 内置过滤器
1. currency将数值格式化为货币格式
2. date日期格式化，年（y）、月（M）、日（d）、星期（EEEE/EEE）、时（H/h）、分（m）、秒（s）、毫秒（.sss），也可以组合到一起使用。
3. filter在给定数组中选择满足条件的一个子集，并返回一个新数组，其条件可以是一个字符串、对象、函数
4. json将Javascrip对象转成JSON字符串。
5. limitTo取出字符串或数组的前（正数）几位或后（负数）几位
6. lowercase将文本转换成小写格式
7. uppercase将文本转换成大写格式
8. number数字格式化，可控制小位位数
9. orderBy对数组进行排序，第2个参数可控制方向

代码示例
```
<body ng-app="App">
	<ul ng-controller="DemoController">
		<li>{{price|currency:'￥'}}</li>
		<li>{{now|date:'yyyy/MM/dd hh:mm:ss'}}</li>
		<li>{{items|filter:'s'}}</li>
		<li>{{students|filter:{age: 16} }}</li>
		<li>{{students|json}}</li>
		<li>{{items|limitTo:-1}}</li>
		<li>{{str|uppercase|limitTo:3}}</li>
		<li>{{str|lowercase}}</li>
		<li>{{num|number:2}}</li>
		<li>{{items|orderBy: '':true}}</li>
		<li>{{students|orderBy: 'age': false}}</li>
	</ul>
	<script src="./libs/angular.min.js"></script>
	<script>
		var App = angular.module('App', []);
		App.controller('DemoController', ['$scope', function ($scope) {
			$scope.price = 11.11;
			$scope.now = new Date;
			$scope.items = ['html', 'css', 'js'];
			$scope.students = [
				{name: '小红', age: 16},
				{name: '小明', age: 16},
				{name: '小米', age: 10}
			];
			$scope.str = 'hello Angular';
			$scope.num = '10.2345';
		}]);
	</script>
</body>
```

### 自定义过滤器
- 除了使用AngularJS内建过滤器外，还可以根据业务需要自定义过滤器，通过模块对象实例提供的filter方法自定义过滤器。
- 示例代码
```
<body ng-app="App">
	<div ng-controller="DemoController">
		<h4>{{info|capitalize:123}}{{name}}</h4>
	</div>
	<script src="./libs/angular.min.js"></script>
	<script>
		var App = angular.module('App', []);
		// 自定义过滤器
		App.filter('demo', function () {
			return function (input) {
				console.log('hello' + input);
				return 'hello' + input;
			}
		});
		App.filter('capitalize', function () {
			// console.log(input);
			return function (input, arg2) {
				// console.log(arg2);
				return input[0].toUpperCase() + input.slice(1);
			}
		});
		// 自定义控制器的
		App.controller('DemoController', ['$scope', function ($scope) {
			$scope.name = '小明';
			$scope.info = 'my name is ';
		}]);
	</script>
</body>
```

## 服务
### 内置服务
- $location是对原生Javascript中location对象属性和方法的封装。
```
App.controller('DemoController', ['$scope', '$location', function($scope, $location) {
	$scope.title = '学习$location服务';
	// $location就是angularJS提前封装好的
	// 提供获取地址相关信息的服务
	// console.log($location);
	//绝对路径
	$scope.absUrl = $location.absUrl();
	//路径
	$scope.url = $location.url();
    //获取域名
	$scope.host = $location.host();
	//查询字符串
	$scope.search = $location.search();
	//哈希值
	$scope.hash = $location.hash();
	//协议
	$scope.protocol = $location.protocol();
	//端口
	$scope.port = $location.port();
}]);
```

- \$timeout&\$interval对原生Javascript中的setTimeout和setInterval进行了封装。
```
App.controller('DemoController', ['$scope', '$timeout', '$interval',function ($scope, $timeout, $interval) {
	$timeout(function () {
		// console.log('执行了');
		$scope.msg = '执行了';
	}, 3000);
	// var i = 0;
	var timer = $interval(function () {
		// console.log(++i);
		$scope.now = new Date;
	}, 1000);
	$scope.stop = function () {
		$interval.cancel(timer);
	}
}]);
```

- $filter格式化数据。
```
// $filter是过滤器
App.controller('DemoController', ['$scope', '$filter', function ($scope, $filter) {
	// $filter是九种过滤器中任何一个
	$scope.price = 11.11;
	var currency = $filter('currency');
	$scope.price = currency($scope.price);
	$scope.str = 'hello angular';
	var uppercase = $filter('uppercase');
	$scope.str = uppercase($scope.str);
	$scope.str1 = $filter('limitTo')($scope.str, 2);
}]);
```

- $log打印调试信息
```
// 使用日志服务
App.controller('DemoController', ['$log', function ($log) {
	$log.info('普通信息');
	$log.warn('警告信息');
	$log.error('错误信息');
	$log.log('打印信息');
	$log.debug('调试信息');
}]);
```

- $http用于向服务端发起异步请求。
```
App.controller('StarController', ['$http', '$scope', '$log', function ($http, $scope, $log) {
$http({
	url: 'example.php',
	// method: 'get',
	method: 'post',
	headers: {
		'Content-Type': 'application/x-www-form-urlencoded'
	},
	params: { // get 参数
		name: 'itcast',
		sex: '男'
	},
	// data: 'age=10'
	data: { // post 传参
		age: 10
	}
}).success(function (info) {
	// info 就是返回的数据
	$log.info(info);
});
}]);
App.controller('DemoController', ['$http', '$scope', function ($http, $scope) {
	$http({
		url: 'jsonp.php?a=JSON_CALLBACK',
		method: 'jsonp' // 采用JSONP方式
	}).success(function (info) {
		console.log(info);
	});
}]);
```

### 自定义服务
- factory方法
```
App.factory('showTime', ['$filter', function ($filter) {
	var now = new Date();
	var date = $filter('date');
	return {
		now: date(now, 'y-M-d H:m:s')
	}
}]);

App.controller('DemoController', ['$scope', 'showTime', function($scope, showTime) {
	$scope.now = showTime.now;
}])
```

- service方法
```
// 自定义服务显示日期
App.service('showTime', ['$filter', function($filter) {
	var now = new Date();
	var date = $filter('date');
	this.now = date(now, 'y-M-d H:mm:ss');
}]);

App.controller('DemoController', ['$scope', 'showTime', function($scope, showTime) {
	$scope.now = showTime.now;
}])
```

- value方法定义常量
```
// 自定义常量服务
App.value('author', 'itcast');
App.value('version', '1.0');
// 本质上一个服务
// 从表现形式上是一个常量
// 常量就是不变的值与变对量相对应
// 声明依赖调用服务
App.controller('DemoController', ['$scope', 'author', 'version', function($scope, author, version) {
	$scope.author = author;
	$scope.ver = version;
}]);
```

## 路由
### 原理 
- 实现单页面调转，使用锚链接，在单一页面中可以通过hashchange事件监听到锚点的变化，进而可以为不同的锚点准备不同的视图,angular对这一原理进行了封装，将锚点的变化封装成路由(Route)

### 使用
- 引入angular-route.js
- 实例化模块APP时，当成依赖传进去，模块名称交ngRoute
- 配置路由模块
- 布局模板 通过ng-view指令布局模板，路由匹配的视图会被加载渲染到区域
- 监听事件变化示例代码
```
// 监听锚点变化然后发送请求
// hashchange事件可以监听锚点变化
window.addEventListener('hashchange', function () {
	// console.log(1);
	// 获取锚点
	var hash = location.hash;
	// 处理#
	hash = hash.slice(1);
	// 实例对象
	var xhr = new XMLHttpRequest;
	// 将锚点做为参数传递给服务端进处理
	xhr.open('get', '10-01.php?hash=' + hash);
	xhr.send(null);
	xhr.onreadystatechange = function () {
		if(xhr.readyState == 4 && xhr.status == 200) {
			var result = xhr.responseText;
			// 将返回结果添加到页面
			document.querySelector('.content').innerHTML = result;
		}
	}
});
```

### 路由参数
- 提供when和otherwise两个方法匹配路由，otherwise作为when的补充只需要一个参数，when可以多次调用，两个参数
    + 第一个参数是一个字符串，代表URL中的hash值
    + 第二个参数是一个对象，配置当前路由的参数，如视图、控制器等
        * a、template 字符串形式的视图模板
	    * b、templateUrl 引入外部视图模板
	    * c、controller 视图模板所属的控制器
	    * d、redirectTo跳转到其它路由
- 获取参数，在控制中注入$routeParams可以获取传递的参数
```
// 依赖ngRoute模块
var App = angular.module('App', ['ngRoute']);
// 需要对路由模块进行配置，使其正常工作
App.config(['$routeProvider', function ($routeProvider) {
	$routeProvider.when('/index', {
		// template: '<h1>index Pages!</h1>',
		templateUrl: './abc.html'
	})
	.when('/list', {
		templateUrl: './list.html', // 视图模板
		controller: 'ListController' // 定义控制器
	})
	.otherwise({
		redirectTo: '/index'
	});
}]);
// 列表控制器
App.controller('ListController', ['$scope', '$http', function ($scope, $http) {
	// 模型数据
	// $scope.items = ['html', 'css', 'js'];
	$http({
		url: '10-02.php',
	}).success(function (info) {
		// console.log(info);
		$scope.items = info;
	});

}]);

// 提供了一个专门负责获取参数的一个服务$routeParams
App.controller('IndexController', ['$scope', '$http', '$routeParams', function ($scope, $http, $routeParams) {
	$scope.content = '练习路由功能';
	console.log($routeParams);
}]);

```


