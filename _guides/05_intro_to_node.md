---
title: Intro to Node.js
category: Intro to Web Dev
date: 2017-02-18 03:35:00 -0800
post_number: 4
---

So far, you've dealt with front-end web development -- code that runs in the
browser. No we'll change gears and dive introduce back-end web development
using Node.js. Node is used to program servers and develop web APIs.
In essence, the backed handles sensitive information and complicated,
computationally expensive operations that cannot run on the browser due to
security concerns or performance limitations.


# How does a Web Server Work?

Users connect to a web server using a protocol (HTTP, FTP), and the server
provides a response. This response could be a web page, files, or any other
kind of data.

Using packages, Node abstracts many of the details of web development.

# The Structure of a Node Server
Your Node server project will include a `package.json` file, a `node_modules`
folder, and JavaScript files with your server code.

`package.json` includes metadata for your Node server, including your
required modules. Node needs this metadata to configure your web server
and install dependencies. Note that you can set up `package.json` with the
command `npm init`

Node automatically generates the `node_modules` folder when it installs
dependencies. It contains code for the dependencies.

# Running Node
First, install Node from the [official Node website](https://nodejs.org/en/download/).

Next, navigate to your project folder and run `npm init` in order to set up
`package.json` (`npm` stands for Node Package Manager).

Write the code for your project within JavaScript files. Make sure to update
the `dependencies` section of `package.json` whenever you require a new module.

Before you can run the server, run `npm install`. This installs all
modules in the `dependencies` section of `package.json`.

Start your server with the command `node <filename>`.

# Hello World

To demonstrate how Node works, we'll create a simple REST API server. Through
a REST API, clients can communicate with the server and exchange data, usually
in the form of JSON. The client calls an API function by issuing a request
to a URL, for example `http://server.address/myRestFunction`

In `server.js`:
{% highlight javascript %}
// DEPENDENCIES -- place required modules at the beginning JavaScript files
var express = require("express"); // Framework for web apps
var cors = require("cors");
var bodyParser = require("body-parser");
var rest = require("./rest.js");

// ENVIRONMENT VARIABLES
const port = process.env.PORT || 2000;

// INITIALIZE EXPRESS
var app = express();
app.use(cors());
app.use(bodyParser.json());
app.use(bodyParser.urlencoded({ extended: true }));
app.use(express.static("public"));
app.use("/", rest);

// START EXPRESS
var server = app.listen(port, function() {
  var host = server.address().address;
  var port = server.address().port;
  console.log("Server listening at http://%s:%s", host, port);
});
{% endhighlight %}

In 'rest.js'
{% highlight javascript %}
var router = require("express").Router();

// Responds with the message supplied by the client
function echo(req, res) {
  var message = req.query.message; // Gets the message parameter
  console.log(message);
  var success = true; // Everything went well server-side
  // Respond wih JSON
  if(success) {
    res.status(200).json({
      result: message
    });
  } else {
    res.status(400).json({
      error: "Something went wrong"
    });
  }
}

router.post("/echo", echo);
module.exports = router;
{% endhighlight %}

Configure the `package.json`, install dependencies using `npm install`, and
run the server locally using `node server.js`.
Then submit a POST request to http://localhost:2000/echo.
By setting the parameter `message`, the server will return different responses
in JSON format.

# Thoughts and Tips

- Running the command `node` launches an interactive console similar to the
interactive python interpreter.
- Modules are powerful, but dangerous. Modules often depend on other modules,
so a security vulnerability in one module can affect many other modules
and therefore many more web applications. Excessive modules are also
inefficient and slow down your server.
