---
layout: post
title:  "NodeJs And PM2: Advanced, production process manager for Node.js "
date:  2017-02-25 17:46:07
categories: tungns update
tags: redis node cache
image: /images/nodejs.png
description: "A Complete feature set for production environment, built with a worldwide community of developers and enterprises"
author: "tungns"
---
In this port, i will help you using pm2.

Create package.json

``` javascript

```

``` javascript
{
  "name": "helloworld",
  "version": "1.0.0",
  "description": "Express helloworld app",
  "main": "app.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "Nguyen Tung",
  "license": "",
  "dependencies": {
    "express": "^4.14.0",
  }
}
```

Continue create file app.js


``` javascript
var express = require('express');
var app = express();
 
app.get('/', function (req, res) {
  res.send('Hello World!');
});
 
app.set('port', process.env.PORT || 3000);
 
app.listen(app.get('port'), function () {
  console.log('Example app listening on port ' + app.get('port'));
});
```

Ok, test run :

``` javascript
  $node app.js 
  Example app listening on port 3000
```

After `npm install pm2 -g`. Done, try command run

``` javascript

  pm2 start app.js
  
```
How many node app run??

``` javascript

  pm2 list
  
```

How to view log

``` javascript

  pm2 logs 0
  
```

Add an instance of the app running on port 3001

``` javascript

PORT=3001 pm2 start -f app.js
  
```

p/s : Why must run more than one instance? You have a very dragon server and you do not want it only runs one app instance, you create multiple instances and load balance them.

See the status of app resource use
``` javascript
pm2 monit
  
```



ex : stop app, delete app, …
Ref: https://github.com/Unitech/pm2#commands-overview
