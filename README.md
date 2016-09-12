# angular-learning
### 学习angular的基本原理和认知

### 什么是AngularJS
```
AngularJS 最初由 Misko Hevery 和 Adam Abrons 于 2009 年开发，后来成为了Google 公司的项目。 AngularJS 弥补了 HTML

在构建应用方面的不足，其通过使用标识符（directives）结构，来扩展 Web 应用中的 HTML 词汇，使开发者可以使用 HTML 来声

明动态内容，从而使得 Web 开发和测试工作变得更加容易。
```

### AngularJS 版本简介
请参考github(https://github.com/angular/angular.js/releases/)

### AngularJS 功能
AngularJS 是专门为应用程序设计的 HTML。

AngularJS 使得开发现代的单一页面应用程序（SPAs：Single Page Applications）变得更加容易。

1  AngularJS 把应用程序数据绑定到 HTML 元素。

2  AngularJS 可以克隆和重复 HTML 元素。

3  AngularJS 可以隐藏和显示 HTML 元素。

4  AngularJS 可以在 HTML 元素"背后"添加代码。

5  AngularJS 支持输入验证

### AngularJS 主要特性
1.MVC

2.模块化与依赖注入

3.双向数据绑定

4.指令与 UI 控件

### AngularJS 资源
[官方网站](http://Angularjs.org)

[AngularJS中文社区](http://www.angularjs.cn/)

[学习分享平台](http://www.ngnice.com/)

[github](https://github.com/angular)

### AngularJS 下载
(http://www.bootcdn.cn/angular.js/)

或者通过nodejs的npm下载：npm install angular

### 使用AngularJS 
1. 下载加载 angular.js 库

2. 使用 ng-app 指令告诉 angular 应该管理 DOM 中的哪一些部分

3. HTML5 允许扩展的（自制的）属性，以  data- 开头。

AngularJS 属性以  ng- 开头，但是您可以使用  data-ng- 来让网页对 HTML5 有效。

### AngularJS 常用指令
* ng_app：
ng-app 指令定义了 AngularJS 应用程序的 根元素。

ng-app 指令在网页加载完毕时会自动引导（自动初始化）应用程序。

* ng-model： 

ng-model 指令 绑定 HTML 元素 到应用程序数据。

也可以

为应用程序数据提供类型验证（number、email、required）

为应用程序数据提供状态（invalid、dirty、touched、error）

为 HTML 元素提供 CSS 类

绑定 HTML 元素到 HTML 表单

* ng_bind指令等同于{{}}：

绑定 HTML 元素到应用程序数据。

示例：
```
<!DOCTYPE html>

<html>

<body>

<div ng-app="">

  <p>在输入框中尝试输入：</p>

  <p>姓名：<input type="text" ng-model="name"></p>

  <p ng-bind="name"></p>

</div>

<script src="angular.min.js"></script>

</body>

</html>
```

示例讲解：

当网页加载完毕，AngularJS 自动开启；

ng-app 指令告诉 AngularJS，<div> 元素是 AngularJS  应用程序 的"所有者"；

ng-model 指令把输入域的值绑定到应用程序变量 name；

ng-bind 指令把应用程序变量 name 绑定到某个段落的 innerHTML。

* ng-init：

ng-init 指令为 AngularJS 应用程序定义了 初始值。

通常情况下，不使用 ng-init。您将使用一个控制器或模块来代替它。

### AngularJS 表达式
AngularJS 表达式写在双大括号内：{{ expression }}。

AngularJS 表达式把数据绑定到 HTML，这与 ng-bind 指令有异曲同工之妙。

AngularJS 将在表达式书写的位置"输出"数据。

AngularJS 表达式 很像 JavaScript  表达式：它们可以包含文字、运算符和变量。

### AngularJS 控制器

AngularJS 控制器 控制 AngularJS 应用程序的数据；

AngularJS 控制器是常规的 JavaScript 对象；

AngularJS 应用程序被控制器控制；

ng-controller 指令定义了应用程序控制器；

控制器是 JavaScript 对象，由标准的 JavaScript 对象的构造函数 创建。

控制器的 $scope 是控制器所指向的应用程序 HTML 元素。

angular 中$scope 是连接 controllers(控制器)和 templates(模板 view/视图)的主要胶合体。

我们可以把我们的 model 存放在 scope 上，来达到双向你绑定。


示例：
```
<!DOCTYPE html>

<html>

<body>

<div ng-app="" ng-controller="personController">

  名: <input type="text" ng-model="person.firstName"><br>
  
  姓: <input type="text" ng-model="person.lastName"><br>
  
  <br>
  
  姓名: {{person.fullName()}}
  
</div>

<script>

function personController($scope) {

  $scope.person = {
  
    firstName: "John",
    
    lastName: "Doe",
    
    fullName: function() {
    
      var x = $scope.person;
      
      return x.firstName + " " + x.lastName;
      
    }
    
  };
  
}
</script>
```

示例讲解：
AngularJS 应用程序由 ng-app 定义。应用程序在 <div> 内运行；

ng-controller 指令把控制器命名为 object；

函数 personController 是一个标准的 JavaScript 对象的构造函数；

控制器对象有一个属性：$scope.person；

person 对象有两个属性：firstName 和 lastName；

ng-model 指令绑定输入域到控制器的属性（firstName 和 lastName）。

* ng-repeat：
ng-repeat指令结合ng-controller

示例：
```
<div ng-app="" ng-controller="namesController">

  <ul>
  
    <li ng-repeat="x in names">
    
      {{ x.name + ', ' + x.country }}
      
    </li>
    
  </ul>
  
</div>

<script src="namesController.js"></script>

<script>

function namesController($scope) {

  $scope.names = [
  
    {name:'Jani',country:'Norway'},
    
    {name:'Hege',country:'Sweden'},
    
    {name:'Kai',country:'Denmark'}
    
  ];
  
}
</script>
```

### AngularJS 应用程序
您的应用程序至少应该有一个模块文件，一个控制器文件。

首先，创建模块文件 "myApp.js"：

```
var app = angular.module("myApp", []);
```

然后，创建控制器文件。本实例中是 "myCtrl.js"：
```
app.controller("myCtrl", function($scope) {

  $scope.firstName = "John";
  
  $scope.lastName = "Doe";
  
});
```

最后，编辑 HTML 引入模块：
```
<!DOCTYPE html>

<html>

<body>

<div ng-app="myApp" ng-controller="myCtrl">

  {{ firstName + " " + lastName }}
  
</div>

<script src="angular.min.js"></script>

<script src="myApp.js"></script>

<script src="myCtrl.js"></script>

</body>

</html>
```





