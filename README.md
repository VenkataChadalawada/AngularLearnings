# AngularLearnings
#### simple Angular example
```html
<!DOCTYPE html>
<html>
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
<body>

<div ng-app="">
 
<p>Input something in the input box:</p>
<p>Name : <input type="text" ng-model="name" placeholder="Enter name here"></p>
<h1>Hello {{name}}</h1>

<p>Input something in the input box2:</p>
<p>Name2: <input type="text" ng-model="name2"></p>
<p ng-bind="name2"></p>

</div>

</body>
</html>

```
### 1 Directives
- basics of AngularJS: directives, expressions, filters, modules, and controllers
- AngularJS extends HTML attributes with Directives, and binds data to HTML with Expressions.
- AngularJS extends HTML with ng-directives.
- The ng-app directive defines an AngularJS application.
- The ng-model directive binds the value of HTML controls (input, select, textarea) to application data.
- The ng-bind directive binds application data to the HTML view.
- The ng-init directive initializes AngularJS application variables

```html 
<!DOCTYPE html>
<html>
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
<body>

<div ng-app="" ng-init="firstName='John'">

<p>The name is <span ng-bind="firstName"></span></p>

</div>

</body>
</html>
```
###### ng-repeat
```html
<!DOCTYPE html>
<html>
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
<body>

<div ng-app="" ng-init="names=['Jani','Hege','Kai']">
  <p>Looping with ng-repeat:</p>
  <ul>
    <li ng-repeat="x in names">
      {{ x }}
    </li>
  </ul>
</div>

<div ng-app="" ng-init="names=[
{name:'Jani',country:'Norway'},
{name:'Hege',country:'Sweden'},
{name:'Kai',country:'Denmark'}]">

<ul>
  <li ng-repeat="x in names">
    {{ x.name + ', ' + x.country }}
  </li>
</ul>

</div>

</body>
</html>
```

####### ng-app
- The ng-app directive defines the root element of an AngularJS application.
- The ng-app directive will auto-bootstrap (automatically initialize) the application when a web page is loaded.

###### ng-init
- The ng-init directive defines initial values for an AngularJS application.
- Normally, you will not use ng-init. You will use a controller or module instead.

###### ng-model
- The ng-model directive binds the value of HTML controls (input, select, textarea) to application data.
- The ng-model directive can also:
  - Provide type validation for application data (number, email, required).
  - Provide status for application data (invalid, dirty, touched, error).
  - Provide CSS classes for HTML elements.
  - Bind HTML elements to HTML forms.

### 2 Expressions
- AngularJS `expressions` are written inside double braces: {{ expression }}.
- AngularJS will "output" data exactly where the expression is written:
- AngularJS expressions bind AngularJS data to HTML the same way as the ng-bind directive
- AngularJS expressions can be written inside double braces: {{ expression }}.
- AngularJS expressions can also be written inside a directive: ng-bind="expression".
- AngularJS will resolve the expression, and return the result exactly where the expression is written.
- AngularJS expressions are much like JavaScript expressions: They can contain literals, operators, and variables.

Example {{ 5 + 5 }} or {{ firstName + " " + lastName }}

```html
<!DOCTYPE html>
<html>
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
<body>

<div ng-app="">
  <p>Name: <input type="text" ng-model="name"></p>
  <p>{{name}}</p>
  <p>My first expression: {{ 5 + 5 }}</p>
</div>

</body>
</html>
```
other examples resolving with `ng-init`
```html
<!DOCTYPE html>
<html>
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
<body>

<div ng-app="">
  <p>My first expression: {{ 5 + 5 }}</p>
</div>

<div ng-app="" ng-init="myCol='lightblue'">
  <input style="background-color:{{myCol}}" ng-model="myCol">
</div>

<div ng-app="" ng-init="quantity=1;cost=5">
  <p>Total in dollar: {{ quantity * cost }}</p>
</div>

<div ng-app="" ng-init="quantity=1;cost=5">
  <p>Total in dollar: <span ng-bind="quantity * cost"></span></p>
</div>

<div ng-app="" ng-init="firstName='John';lastName='Doe'">
  <p>The name is {{ firstName + " " + lastName }}</p>
</div>

<div ng-app="" ng-init="firstName='John';lastName='Doe'">
  <p>The name is <span ng-bind="firstName + ' ' + lastName"></span></p>
</div>

<div ng-app="" ng-init="person={firstName:'John',lastName:'Doe'}">
  <p>The name is {{ person.lastName }}</p>
</div>

<div ng-app="" ng-init="person={firstName:'John',lastName:'Doe'}">
  <p>The name is <span ng-bind="person.lastName"></span></p>
</div>

<div ng-app="" ng-init="points=[1,15,19,2,40]">
  <p>The third result is {{ points[2] }}</p>
</div>

<div ng-app="" ng-init="points=[1,15,19,2,40]">
  <p>The third result is <span ng-bind="points[2]"></span></p>
</div>

</body>
</html>
```


### 3 Modules & Controllers
- AngularJS modules define AngularJS applications.
- AngularJS controllers control AngularJS applications.
- The ng-app directive defines the application, the ng-controller directive defines the controller.
- An AngularJS module defines an application.
- The module is a container for the different parts of an application.
- The module is a container for the application controllers.

Controllers always belong to a module

``` html
<!DOCTYPE html>
<html>
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
<body>

<p>Try to change the names.</p>

<div ng-app="myApp" ng-controller="myCtrl">

First Name: <input type="text" ng-model="firstName"><br>
Last Name: <input type="text" ng-model="lastName"><br>
<br>
Full Name: {{firstName + " " + lastName}}

</div>

<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope) {
    $scope.firstName= "John";
    $scope.lastName= "Doe";
});
</script>

</body>
</html>
```
##### Two way binding with Model
```html
<!DOCTYPE html>
<html>
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
<body>

<div ng-app="myApp" ng-controller="myCtrl">
Name: <input ng-model="name">
<h1>You entered: {{name}}</h1>
</div>

<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope) {
    $scope.name = "John Doe";
});
</script>

<p>Change the name inside the input field, and you will see the name in the header changes accordingly.</p>

</body>
</html>
```

###### Validate user input
The ng-model directive can provide type validation for application data (number, e-mail, required):
```html
<!DOCTYPE html>
<html>
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
<body>

<form ng-app="" name="myForm">
    Email:
    <input type="email" name="myAddress" ng-model="text">
    <span ng-show="myForm.myAddress.$error.email">Not a valid e-mail address</span>
</form>

<p>Enter your e-mail address in the input field. AngularJS will display an errormessage if the address is not an e-mail.</p>

</body>
</html>
```

##### Application status
The ng-model directive can provide status for application data (valid, dirty, touched, error):
``` html
<!DOCTYPE html>
<html>
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
<body>

<form ng-app="" name="myForm" ng-init="myText = 'post@myweb.com'">

Email:
<input type="email" name="myAddress" ng-model="myText" required>
<p>Edit the e-mail address, and try to change the status.</p>
<h1>Status</h1>
<p>Valid: {{myForm.myAddress.$valid}} (if true, the value meets all criteria).</p>
<p>Dirty: {{myForm.myAddress.$dirty}} (if true, the value has been changed).</p>
<p>Touched: {{myForm.myAddress.$touched}} (if true, the field has been in focus).</p>

</form>

</body>
</html>
```

###### The ng-model directive provides CSS classes
The ng-model directive provides CSS classes for HTML elements, depending on their status:
```html
<!DOCTYPE html>
<html>
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
<style>
input.ng-invalid {
    background-color: lightblue;
}
</style>
<body>

<form ng-app="" name="myForm">
    Enter your name:
    <input name="myName" ng-model="myText" required>
</form>

<p>Edit the text field and it will get/lose classes according to the status.</p>
<p><b>Note:</b> A text field with the "required" attribute is not valid when it is empty.</p>

</body>
</html>

```

The ng-model directive adds/removes the following classes, according to the status of the form field:

  - ng-empty
  - ng-not-empty
  - ng-touched
  - ng-untouched
  - ng-valid
  - ng-invalid
  - ng-dirty
  - ng-pending
  - ng-pristine
  
### data binding
Because of the immediate synchronization of the model and the view, the controller can be completely separated from the view, and simply concentrate on the model data. Thanks to the data binding in AngularJS, the view will reflect any changes made in the controller. 
```html
<!DOCTYPE html>
<html>
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
<body>

<div ng-app="myApp" ng-controller="myCtrl">
    <h1 ng-click="changeName()">{{firstname}}</h1>
</div>

<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope) {
    $scope.firstname = "John";
    $scope.changeName = function() {
        $scope.firstname = "Nelly";
    }
});
</script>

<p>Click on the header to run the "changeName" function.</p>

<p>This example demonstrates how to use the controller to change model data.</p>

</body>
</html>

```

- AngularJS applications are controlled by controllers.
- The ng-controller directive defines the application controller.
- A controller is a JavaScript Object, created by a standard JavaScript object constructor.

``` html
<!DOCTYPE html>
<html>
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
<body>

<div ng-app="myApp" ng-controller="personCtrl">

First Name: <input type="text" ng-model="firstName"><br>
Last Name: <input type="text" ng-model="lastName"><br>
<br>
Full Name: {{fullName()}}

</div>

<script>
var app = angular.module('myApp', []);
app.controller('personCtrl', function($scope) {
    $scope.firstName = "John";
    $scope.lastName = "Doe";
    $scope.fullName = function() {
        return $scope.firstName + " " + $scope.lastName;
    };
});
</script>

</body>
</html>

```
##### controller in external files
```html
<div ng-app="myApp" ng-controller="personCtrl">

First Name: <input type="text" ng-model="firstName"><br>
Last Name: <input type="text" ng-model="lastName"><br>
<br>
Full Name: {{fullName()}}

</div>

<script src="personController.js"></script>

```
personController.js
```javascript
angular.module('myApp', []).controller('namesCtrl', function($scope) {
  $scope.names = [
    {name:'Jani',country:'Norway'},
    {name:'Hege',country:'Sweden'},
    {name:'Kai',country:'Denmark'}
  ];
});
```

### SCOPE
The scope is the binding part between the HTML (view) and the JavaScript (controller).

The scope is an object with the available properties and methods.

The scope is available for both the view and the controller.
```html
<!DOCTYPE html>
<html>
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
<body>

<div ng-app="myApp" ng-controller="myCtrl">

<h1>{{carname}}</h1>

</div>

<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope) {
    $scope.carname = "Volvo";
});
</script>

<p>The property "carname" was made in the controller, and can be referred to in the view by using the {{ }} brackets.</p>

</body>
</html>
```

- When adding properties to the $scope object in the controller, the view (HTML) gets access to these properties.
- In the view, you do not use the prefix $scope, you just refer to a property name, like {{carname}}.
- If we consider an AngularJS application to consist of:
  - View, which is the HTML.
  - Model, which is the data available for the current view.
  - Controller, which is the JavaScript function that makes/changes/removes/controls the data.
  - Then the scope is the Model.

-The scope is a JavaScript object with properties and methods, which are available for both the view and the controller.

```html
<!DOCTYPE html>
<html>
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
<body>

<div ng-app="myApp" ng-controller="myCtrl">

<ul>
  <li ng-repeat="x in names">{{x}}</li>
</ul>

</div>

<script>
var app = angular.module('myApp', []);

app.controller('myCtrl', function($scope) {
    $scope.names = ["Emil", "Tobias", "Linus"];
});
</script>

<p>The variable "x" has a different value for each repetition, proving that each repetition has its own scope.</p>

</body>
</html>
```
##### Rootscope
- All applications have a $rootScope which is the scope created on the HTML element that contains the ng-app directive.

- The rootScope is available in the entire application.

- If a variable has the same name in both the current scope and in the rootScope, the application uses the one in the current scope.

```html
<!DOCTYPE html>
<html>
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
<body ng-app="myApp">

<p>The rootScope's favorite color:</p>
<h1>{{color}}</h1>

<div ng-controller="myCtrl">

<p>The scope of the controller's favorite color:</p>
<h1>{{color}}</h1>

</div>

<p>The rootScope's favorite color is still:</p>
<h1>{{color}}</h1>

<script>
var app = angular.module('myApp', []);
app.run(function($rootScope) {
    $rootScope.color = 'blue';
});
app.controller('myCtrl', function($scope) {
    $scope.color = "red";
});
</script>

<p>Notice that controller's color variable does not overwrite the rootScope's color value.</p>

</body>
</html>

```
