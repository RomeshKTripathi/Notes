
# Fundamentals
### About
- Node.js is an open source server environment.
- Node.js allows to run JavaScript on the server.

Here is how PHP or ASP handles a file request:

```Sends the task to the computer's file system.
Waits while the file system opens and reads the file.
Returns the content to the client.
Ready to handle the next request.
```
Here is how Node.js handles a file request:
```
Sends the task to the computer's file system.
Ready to handle the next request.
When the file system has opened and read the file, the server returns the content to the client.
```
> Node.js eliminates the waiting, and simply continues with the next request.

### What Can Node.js Do?
1. Node.js acan generate dynamic page content.
2. Node.js can _create_, _open_, _read_, _write_, _delete_ and _close_ files on server.
3. Node.js can collect form data.
4. Node.js can _add_, _delete_, _modify_ data in your database.

### What is Node.js File?
1. Node.js files contain tasks that will be executed on certain events.
2. A typical events is someone trying to access a port on the server.
3. Node.js files must be initiated on the server before having any effect

## Getting Started With `Node.js`
> Download and install Node.js
```js
var http = require('http');

http.createServer(function (req, res) {
  res.writeHead(200, {'Content-Type': 'text/html'});
  res.end('Hello World!');
}).listen(8080);
```
save the file with FILE_NAME.js extension and run : node FILE_NAME.js command in terminal.

## Module in Node.js

Consider modules to be the same as _JavaScript_ libraries.
A set of functions you want to include in your application.

> [!NOTE]
> Node.js has a set of built-in modules which you can use without any further installation.

### Include Modules
To include a module, use the `require("MODULE_NAME")` function;
```js
var http = require('http');
```
now your application has _http_ module, and is able to create a server:
```js
http.createServer(function(req, res){
  res.writeHead(200, {'Content-Type': 'text/html'});
  res.end('Hello World!);
}).listen(4000);

```

## Create your own modules.
Creation of your own module is easy in node.js.
```js
exports.myDateTime = function(){
  return Date();
}
```
use of `exports` keyword make properties and methods available outside the module file.

```js
const dt = require('./myDateTime');
// now you can use this module in your application.
```

## `http` Module
**_http_** module allows _Node.js_ to transfer data over the HTTP(_Hyper Text Transfer Protocol_ 

```js
var http = require('http');
```
now create your server with `createServer()`

```js
// http.createServer(CALLBACK_FUNCTION).listen(PORT);

http.createServer(function(req, res){
res.write('Hello World!'); // write a response to client.
res.end(); // ends the response
}).listen(8000);

```
### _http_ header
if response from http server is supposed to be displayed as HTML, you should include an HTTP header.

```js
const http = require('http');

http.createServer(function(req, res){
  res.writeHead(200, {'Content-Type':'text/html'});
  res.write('Hello World!');
  res.end();
}).listen(8000);
```

### Query Stirng
```js
var http = require('http');
http.createServer(function (req, res) {
  res.writeHead(200, {'Content-Type': 'text/html'});
  res.write(req.url);
  res.end();
}).listen(8080);
```
### Spliting the query string
```js
var http = require('http');
var url = require('url');

http.createServer(function (req, res) {
  res.writeHead(200, {'Content-Type': 'text/html'});
  var q = url.parse(req.url, true).query;
  var txt = q.year + " " + q.month;
  res.end(txt);
}).listen(8080);
```

```
Output on :http://localhost:8080/?year=2017&month=July
2017 July
```

## File System in Node.js
```js
const fs = require('fs')
```

Common use for file system module.
1. Read files
2. Create Files
3. Update Files
4. Delete Files
5. Rename Files

```js
var http = require('http');
var fs = require('fs');
http.createServer(function (req, res) {
  fs.readFile('demofile1.html', function(err, data) {
    res.writeHead(200, {'Content-Type': 'text/html'});
    res.write(data);
    return res.end();
  });
}).listen(8080);
```
### Create Files
`fs.appendFile()`
`fs.open()`
`fs.writeFile()`

the `fs.appendFile()` method appends specified content to a file. If the file does not exist, the file will be created:
```js
var fs = require('fs');

fs.appendFile('mynewfile1.txt', 'Hello content!', function (err) {
  if (err) throw err;
  console.log('Saved!');
});
```

```
The fs.open() method takes a "flag" as the second argument, if the flag is "w" for "writing", the specified file is opened for writing. If the file does not exist, an empty file is created:
```
The fs.writeFile() method replaces the specified file and content if it exists. If the file does not exist, a new file, containing the specified content, will be created:
```js
var fs = require('fs');

fs.open('mynewfile2.txt', 'w', function (err, file) {
  if (err) throw err;
  console.log('Saved!');
});
```


