---
title: Intro to JavaScript
category: Intro to Web Dev
date: 2017-02-11 01:05:00 -0800
post_number: 4
---

JavaScript is a Turing complete programming language running in the web browser.
Through JavaScript, a simple web page can become an advanced application
capable of adding almost unlimited functionalities. However, this power comes
at a cost; in terms of performance, JavaScript runs more slowly than native
compiled programs. Furthermore, JavaScript's features pose a huge security
concern. Due to these security concerns, many users disable JavaScript in their
browsers breaking features in web pages that depend on JavaScript.

JavaScript development is a challenge; there exist many, fast moving
technologies that developers must be aware of. Furthermore, idiosyncrasies
in the language can make development tedious and troublesome.

# Background
JavaScript's syntax seems oddly familiar; it is influenced by popular
programming languages like Python and C. On the other hand, its roots in Scheme
created an emphasis on functional programming.

Variables are untyped and declared using `var myVariable = "hello, world;"`.
Generally, semicolons follow JavaScript statements, but this is not a strict
requirement.

The syntax for control statements (if, for loops, switches) are similar to
C. Here's a short JavaScript program that prints the even numbers between 1 and
10:
{% highlight javascript %}
for (var i = 1; i < 10; i++) {
  if (i % 2 != 0) {
    console.log(i) // This is a comment
  } /* This is also a comment */
}
{% endhighlight %}

There are 2 ways to declare functions:

1. `function sayHello(arg1) { /* Function body */ }`
2. `var sayHello = function(arg1, arg2) { /* Function body */ }`

Often, functions are passed as arguments to other functions. Nested
function are quite common.

# Running JavaScript
Most modern web browsers contain JavaScript consoles, usually accessed by
pressing F12. Within this console, you can execute JavaScript code similar
to the interactive Python command prompt. Custom JavaScript run in the console
can also interact with the browser's current website which can be useful
in debugging scripts.

# Data types
While JavaScript is untyped, variables can only be assigned to a limited
set of data types:

- Boolean: True/False value
- Null: an invalid variable
- Undefined: automatically assigned to variables upon declaration
- Number: 1, 2, 0x5e, 2.97e6
- String: a collection of characters
- Array: a list of values, e.g. `[1, "hello", function(a) { console.log(a); }, False]`
- Object

# Objects
Objects are JavaScript's replacement for classes and allow for object oriented
programming. They serve as a general data structure that contains data and
functions.
Create objects with the object literal {}:

{% highlight javascript %}
var tiger = {
  name: "Henry", // tiger.name = Henry
  roar: function() { console.log("ROAR!"); },
  age: 13,  // don't forget the comma between object properties
  favoriteFood: "broccoli"
}
{% endhighlight %}

Access object properties in 2 ways:

1. `object.property` e.g. `tiger.name`
2. `object["property"]` e.g. `tiger["name"]`

The second method is particularly useful when iterating through an unknown
object's properties:
{% highlight javascript %}
for (var key in tiger) {
  console.log(key + ": " + tiger[key]);
}
// Alternative loop using forEach on the list of properties
Object.keys(tiger).forEach(function(key, index) {
  console.log(key + ": " + tiger[key])
});
{% endhighlight %}

# Object Constructors
A downside of the `{}` approach to creating objects is that it prevents
dynamic object creation from arguments. The workaround exploits the `this`
keyword, which [works in many different ways](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this).
Essentially, we create a new `this` for the function call. We then assign
the desired object properties to `this`. The function call returns `this`,
and our variable is set to the new object.
An advantage of this approach is inheritance:
{% highlight javascript %}
function Animal(name, age, favoriteFood) {
  this.name = name;
  this.age = age;
  this.favoriteFood = favoriteFood;
}
function Tiger(name, age) { // Tiger inherits from Animal
  Animal.call(name, age, "broccoli"); // Parent constructor
  this.roar = function() { console.log("ROAR!"); }
}

var tigerHarry = new Tiger("Harry", 3); // create a tiger
{% endhighlight %}

# Miscellaneous Thoughts and Tips
- Although we've covered the fundamentals of the language, we've barely
scratched the surface of JavaScript. There's libraries, JavaScript-HTML-CSS
interaction, more advanced features, and web technologies that I've left out in
the interest of brevity.
- JavaScript provides a lot of built-in methods and objects, such as the string
manipulation methods as well as Date and Math objects.
- Minimize the use of nested functions. They reduce code legibility which can make debugging and code maintenance painful.
- Comment your code. JavaScript is a verbose language, so comments will
facilitate debugging and future work on the code base.

# References
- [Mozilla Developer Network's JavaScript Reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference) -- the gold standard for JavaScript reference. The documentation is clear,
concise, and easy to understand. Furthermore, Netscape, the predecessor to
Mozilla's Firefox browser was the first to implement JavaScript.
- [W3Schools JavaScript and HTML DOM Reference] -- explains JavaScript
interaction with HTML.
