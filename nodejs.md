# Node.js

* Is a `Runtime environment` build on top of V8 Engine in 2009.
* runs Javascript code outside the browser.

* Single threaded 
* Asynchronous(non-blocking)- does not wait.
* Event driven : Events are run asynchronously. When a event is triggred a callback is fired.

**Note :** We don't have window or document objects. As they are part of browser environment.

## When to use Node

* Any thing that is not CPU intensive. 
* Application that require high throughput. 
* Light weight application with high speed. 
eg : Like building back-end API etc.


## **NPM**

Node package manger used to install 3rd party packages(modules, libraries). Packages installed using npm are stored in `node_modules` folders.
And those packages are stored as dependencies in the `package.json` file. When you deploy your application you can delete the `node_modules` and as the dependencies are already recorded in package.json file.
So you can install those again using `npm install` this will recreate the `node_module` folder.

installing packages in node using npm
```
npm init                     
npm install <package_name> 
```
`npm install` will install all the dependencies in `package.json` file.

## **NVM** 
Used to manage the installation of different node version on your system. You can install any version of nodejs using `nvm install` and use it using `nvm use`.
will install node version 12.16.3
```
nvm install 12.16.3 
nvm use 12.16.3
```
## **Event Loop**

Helps to push intensive operation to a sperate thread,so that only non-blocking operation are on main thread,Multithreaded.

Even loop phases (Macro):
there are 6 phases each have their own callback queue.
 * Timer : Timer callbacks are kept here. Timer callbacks are controlled by poll phase. 
 * pending callbacks : System related callbacks are executed.
 * idle/prepare : Do nothing
 * poll phase : New syncronous input/output callbacks except timer and closing callbacks are executed.
 * check : setImmediate callbacks are executed if nothing is here event will wait in Poll phase
 * close callback : Execute closing event callbacks

There is one more phase which is not part of event loop
* nextTick(micro).

## **Node Module System**

* Every file is a module in nodeJS and function and variable defined in that file is scoped to that file/module and not available outside of that module. 

## **Core Modules in Node commanly used**
modules are already included in node we don't need to install them.
`var file = require('fs')`
### **path**
to work with file and directory path
const path = require('path')
* join() - joins given paths segment together.
* resolve() - resolves given path segments into absolute path
### **fs**
used to manipulate file and directory system.
`var file = require('fs')`
* readFile() - reads content of file  asynchronously 
* writeFile() - if filename is passed writes data to file and will replace it if alreadt exists.
* rename() - used to rename file
* stat() - check if given file exists.
* unlink() - removes file and symbolic link asynchronously
### **os**
This module provides many functions that you can use to retrieve information from the underlying operating system and the computer the program runs on, and interact with it.
### **HTTP**
networking module of nodejs that allows it to communicate it over HTTP.
`const http = require('http')`
* createServer() - create HTTP server.
* writeHead() - send the response http header with specified status code.
* end() - response body.
* listen() - listen to give given hostname at specified port

## **NPM Modules commanly used.**

Are 3-rd party modules that you have to install if you wnat to use them using `npm install`

* express -  is web framework for node.
* nodemon - pushes changes automatically to avoid restarting server.
* moment - formatting date and time.
* axio - promised based http client.

### Module wrapper
wrap file/module before it is executed and it looks like below this helps the variable to be scoped to the module.
```Javascript
(function(exports, require, module, __filename, __dirname) {
// Module code actually lives in here
});
```

## Create local module.
### Export a module
If we want to a access any variable or function in other file the we must export that variable or function so that it can be used by other file.

eg: `module.exports = app` app can be variable or function
 
### Load a module
To load a module use `require()` CommonJS modules which is a  function and pass the name or path of target module that you want to load. Order lookup 1. Built-in core modules 2. NPM modules(modules inside node_module) 3. Local module(./)
eg: `var path = require('path')`

