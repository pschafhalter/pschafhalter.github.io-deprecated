---
title: Intro to CSS
category: Intro to Web Dev
date: 2017-02-10 23:13:00 -0800
post_number: 3
---

While HTML describes the structure of a web page, CSS describes its look and
style. Its uses include setting colors, sizes, positions, paddings, and
margins. Above all, CSS serves as a tool to creating vibrant, visually
appealing web pages.

# 3 Ways of Applying CSS
1. CSS Files.
The preferred way of writing CSS is to create a separate file and include
it in the HTML document. This method results in modular code which makes it
easier to modify the website in the future. Furthermore, multiple HTML
files can include the same CSS file, resulting easy, consistent design
across the website. To include a CSS file in an HTML file,
add the tag `<link rel="stylesheet" href="/my_css_file.css">`.

2. Embedded CSS
This method places CSS code inside an HTML element. The advantage is that
the data for the web page exists on less files. The disadvantage is that it
results in longer files which can result in convoluted code. The CSS code is
included by adding:
{% highlight html %}
<style media="screen" type="text/css">
/* CSS CODE HERE */
</style>
{% endhighlight %}
Usually this is placed within the head of the HTML document.

3. Inline CSS
This method applies styling directly to an individual HTML element. The
advantage of inline CSS is that it's quick to write while coding the HTML
website -- simply add a style attribute to your HTML element and set it to
the relevant CSS code: `<p style="color:blue;">This is a blue paragraph</p>`.
The disadvantage is that it results in even more convoluted code than
embedded CSS, and the redundancy of repeating styles becomes inefficient.

# Styling
General syntax for CSS styling is `property: value;`. Some common properties
include `color`, `background-color`, and `font-size`. CSS is flexible on unit
types -- colors can be set to names, RGB codes, or hexadecimal values.
Distances are in percentages, pixels, em's, and [more](http://www.w3schools.com/cssref/css_units.asp).

# Selectors
The power of CSS lies in its selectors; it can apply the same styling to
many different elements at once. Selectors are used in CSS files or embedded
CSS. The following general formula applies CSS using selectors:
{% highlight css %}
SELECTOR {
  /* Sample styling for the selected elements */
  background-color: orange;
}
{% endhighlight %}

Different selectors have different syntax:
- .id -- .fruit selects all elements with `class="fruit"`
- #class -- #banana selects all elements with `id="banana"`
- * selects all elements
- element1,element2,...,elementn -- h1, h2, #fruit selects all h1 and h2
elements as well as elements of `class="banana"`
- element1>element2 -- .banana > p selects all elements of type p within
elements of `class="banana"`

While the above selectors are most commonly used, [W3Schools CSS Selector Reference](http://www.w3schools.com/cssref/css_selectors.asp)
explains many more CSS selectors.

# Miscellaneous Thoughts and Tips
- Modern CSS contains support for simple "functions" -- simple directives that
assist in styling e.g. applying an animation or rotating an element. Like HTML,
CSS is not a programming language; it functions as a description of an HTML
document's visual look.
- CSS implements many different units that can assist in styling. Colors can be
strings, RGB, or hex codes. To name a few, lengths can be in pixels, ems,
centimeters, millimeters, inches, points.

# Resources
- [W3Schools CSS Reference](http://www.w3schools.com/cssref/default.asp) --
verbose, but contains almost all the information you need for CSS.
- [W3Schools Pseudoclasses
Tutorial](http://www.w3schools.com/css/css_pseudo_classes.asp) -- styles
special states of elements e.g. visited links
