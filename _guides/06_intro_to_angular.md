---
title: Intro to Angular
category: Intro to Web Dev
date: 2017-02-24 03:35:00 -0800
post_number: 5
---

In its purest form, JavaScript interacts with web pages by modifying the
Document Object Model (DOM) -- the browser's internal representation of a
web page. Browsers provide a standard API through the
[Document object](https://developer.mozilla.org/en-US/docs/Web/API/Document).
DOM based programming has disadvantages: it's verbose, doesn't scale well
as the website grows, and makes creating dynamic web applications difficult.

AngularJS is a JavaScript framework which abstracts the creation of dynamic
web applications. Maintained by Google, Angular has become a standard in web
application development.

# What is a Web App?
First, some terms:
- **Front-end** refers to the parts of an application that a web browser
interacts with.
- **Back-end** refers to parts of an application that a client such as web
  browser cannot directly access. In other words, backend is anything related
  to web servers, such as databases, algorithms, and API implementations.

A web app has a front-end that runs in a client's web browser which connects to
a back-end server that stores data and runs computations ("The Cloud").
Facebook, Twitter, Google Search, and GMail are all web applications.

While Angular is front-end (all of its code runs in a web browser),
it provides convenient abstractions to interact with the back-end.

# Getting Started
Add the following tag to your HTML header:
{% highlight html %}
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.4.8/angular.min.js"></script>
{% endhighlight %}
Set the `body` tag of your app to the owner of an Angular app:
{% highlight html %}
<body ng-app="appName">
{% endhighlight %}

# Expressions
Angular automatically substitutes data for expressions within HTML which
simplifies JavaScript-HTML interaction.
An expression is written inside double braces:
`{% raw %}{{ expression_content }}{% endraw %}`.
For example, the expression `<p>{{ 5 + 6 }}</p>` results in `<p>11</p>`.

Expressions are flexible; in addition to HTML elements, they can bind
data to attributes, for example: `<img src="{{ tigerUrl }}">`.
They can also become quite advanced involving for loops

# Modules
A module is a container for an Angular application.
Create a module with the statement
{% highlight javascript %}
var app = angular.module("appName", []);
{% endhighlight %}
Place dependent modules within the `[]`.

# Controllers
A controller manipulates the DOM of a specific HTML element. By setting
properties of the  `$scope` object, the controller can set variables
(including functions) that Angular expressions within the element can access.
For example, `$scope.name = "sk0p3"` sets `{% raw  %}{{ name }}{% endraw %}`
to `sk0p3` in the HTML element.

The following code creates a controller called `MainCtrl`:
{% highlight javascript %}
app.controller("MainCtrl", function($scope) {
    $scope.appName = "Best app";
});
{% endhighlight %}

# Directives
Directives are custom HTML attributes which offer additional functionalities
for the application.
Some important Angular directives
- `ng-app` directive defines the module
which contains the web app.
- `ng-init` initializes JavaScript variables which
Angular expressions can later access.
- `ng-repeat` repeats a certain element.
- `ng-if` only includes a certain element if a condition is true
- `ng-include` loads HTML from a file into the element.

{% highlight javascript %}
<div ng-app="" ng-init="shoppingList=['beans',
  'greens', 'tomatoes', 'potatoes', 'lamb', 'ram']">
Shopping List:
    <ul>
      <li ng-repeat="item in shoppingList">{% raw %}{{ item }}{% endraw %}</li>
    </ul>
</div>
{% endhighlight %}

Angular even allows the declaration of custom directives:
{% highlight javascript %}
app.directive("directiveName", function() {
    return {
        restrict : "A",   // Restricts directive to attributes
        template : "<h1>My directive did this!</h1>"
    };
});
{% endhighlight %}

# Services
Services are objects or functions that can be shared across many different
controllers. Most commonly, services interact with the back-end.
Generally, create a new module for each group of services in order to
keep the app well structured:
{% highlight javascript %}
angular.module('app.serviceName', [])
  .factory("FactoryName", function() {
    return {
      doStuff: function() { console.log("foo"); },
      bestAnimal: "tiger"
    }
  });
{% endhighlight %}

To include this service in your app's main module, include "app.serviceName"
in the list of dependent modules:
{% highlight javascript %}
var app = angular.module("appName", ["app.serviceName"]);
{% endhighlight %}

Controllers will not automatically load services; each factory must be
included separately as an argument to the function that initializes the
controller:
{% highlight javascript %}
app.controller("MainCtrl", function($scope, FactoryName) {
    $scope.appName = "Best app";
    FactoryName.doStuff();
});
{% endhighlight %}

# Suggested Structure of an Angular Web App

{% highlight null %}
index.html -- main HTML document which loads all JavaScript
app/ -- folder containing Angular-related JavaScript
  app.js -- initializes the main module
  controllers.js -- contains controllers
  directives.js -- contains custom directives
  services.js -- contains services
assets/ -- folder containing static content (images, CSS, other JavaScript)
views/ -- HTML files loaded by ng-include
{% endhighlight %}

# Resources
- [W3Schools AngularJS Introduction](https://www.w3schools.com/angular/angular_intro.asp)
- [TutorialsPoint AngularJS Tutorial](https://www.tutorialspoint.com/angularjs/index.htm)
