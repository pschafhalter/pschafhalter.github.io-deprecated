---
title: Intro to HTML
category: Intro to Web Dev
date: 2017-01-23 16:36:00 -0800
post_number: 2
---

HTML structures web pages.
Websites are complicated; they may contain many sections, tables, images,
and other files, and even programs.
Using HTML, we can logically organize this information in a way
legible for humans and computers.

# Tags
Tags define the HTML document.
The purpose of a tag is to classify information.
Any text enclosed between the angle brackets < > is considered a tag;
however, there are only a few valid HTML tags. Note that browsers will
render HTML code even if there are invalid tags -- so watch out for typos!
Most HTML tags evoke a response by the browser, such as
displaying text or displaying an image.
For example, the `<image>` tag defines a picture on the web page.

Many HTML tags work in pairs, with an opening tag, content, and a closing tag.
This sequence forms an element. The following is the basic structure of an element: ```<tag_name>CONTENT</tag_name>```.
Elements can be nested -- in fact the layout of an HTML document requires
the use of nested elements.
For example, the following code displays a paragraph titled "Tigers"
with a nested link to the Wikipedia article on tigers:
{% highlight html %}
<h1>Tigers</h1>
<p><a href="https://en.wikipedia.org/wiki/Tigers">Tigers</a> are
 the largest cats on earth</p>
{% endhighlight %}

Often, tags will have attributes which offer more information
or define behavior for the tag. For example, the `<image>` tag
requires a `src` attribute for the source of the image:
{% highlight html %}
<img src="/tigers.gif">
{% endhighlight %}

Note that the value of the attribute is always in quotes -- these can
either be single ' or double ".

# Comments
Comments follow the form of `<!-- COMMENT HERE -->`.
Comment contents can span multiple lines.

# Special Characters
Because all HTML tags begin with < and end with > a problem arises:
how to display these characters without defining a tag?
HTML solves this by using entities -- sequences of text that the browser
replaces with the desired special character.
They generally follow the formula `&entity_name;` or `&#entity_number;`
For example, `&lt;` and `&gt;` represent < and >.

# Anatomy of an HTML Document
{% highlight html %}
<!DOCTYPE html> <!-- Declares that this is an HTML document -->
<html> <!-- Start of HTML code -->
<head> <!-- Meta-data goes here. Example of meta-data include:
              - Website title
              - Included CSS and JavaScript files and code
              - Search engine optimizations -->
</head>
<body>
<!-- Everything you see goes here -->
</body>
</html>
{% endhighlight %}

# Some Popular HTML Tags

| Tag Name | Description | Example |
| -------- | ----------- | ------- |
| h1,...,h6 | Headings by order of importance | `<h1>Tigers</h1>` |
| p | Paragraph | `<p>To be or not to be</p>` |
| img | Image | `<img src="/tigers.gif">` |
| a | Anchor (usually a link) | `<a href="http://example.com">Example website</a>` |
| div | Division or section | `<div style="color:blue;">Blue text</div>` |
| span | Groups inline elements | `<span style="color:blue;">blue text</span>` |
| button | A button | `<button>Click me!</button>` |


# Lists, tables, forms
Lists, tables, and forms are more complex HTML structures that require nesting.
For example, each list must consist of a a series of list item elements:
{% highlight html %}
Big cats:
<ul> <!-- Start an Unordered List -->
  <li>Tiger</li>
  <li>Lion</li>
  <li>Leopard</li>
</ul>
{% endhighlight %}
Tables are similar -- they nest table data elements within a table row
within the table. Forms require any nested input elements to function.

# FAQ
- What does HTML stand for?
  - HyperText Markup Language. It means a language used to annotate documents
with more than just test.

# Resources
- [HTML Cheat Sheet](http://www.simplehtmlguide.com/cheatsheet.php) -- Quick reference for basic HTML.
- [HTML Dog's List of HTML Tags](http://htmldog.com/references/html/tags/) -- Clean overview of HTML tags.
- [W3Schools' HTML Reference](http://www.w3schools.com/tags/default.asp) -- Not the nicest UI, but the standard for web. Click the next button for many more HTML-related references.
- [W3Schools' HTML Entities](http://www.w3schools.com/html/html_entities.asp)
