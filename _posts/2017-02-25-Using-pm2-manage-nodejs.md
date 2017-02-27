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

  # Fork mode
$ pm2 start app.js --name my-api # Name process

# Cluster mode
$ pm2 start app.js -i 0        # Will start maximum processes with LB depending on available CPUs
$ pm2 start app.js -i max      # Same as above, but deprecated.

# Listing

$ pm2 list               # Display all processes status
$ pm2 jlist              # Print process list in raw JSON
$ pm2 prettylist         # Print process list in beautified JSON

$ pm2 describe 0         # Display all informations about a specific process

$ pm2 monit              # Monitor all processes

# Logs

$ pm2 logs [--raw]       # Display all processes logs in streaming
$ pm2 flush              # Empty all log file
$ pm2 reloadLogs         # Reload all logs

# Actions

$ pm2 stop all           # Stop all processes
$ pm2 restart all        # Restart all processes

$ pm2 reload all         # Will 0s downtime reload (for NETWORKED apps)
$ pm2 gracefulReload all # Send exit message then reload (for networked apps)

$ pm2 stop 0             # Stop specific process id
$ pm2 restart 0          # Restart specific process id

$ pm2 delete 0           # Will remove process from pm2 list
$ pm2 delete all         # Will remove all processes from pm2 list

# Misc

$ pm2 reset <process>    # Reset meta data (restarted time...)
$ pm2 updatePM2          # Update in memory pm2
$ pm2 ping               # Ensure pm2 daemon has been launched
$ pm2 sendSignal SIGUSR2 my-app # Send system signal to script
$ pm2 start app.js --no-daemon
$ pm2 start app.js --no-vizion
$ pm2 start app.js --no-autorestart
42 starts

ndlr; 42 is the answer to life, the universe and everything.

$ pm2 start app.js           # Start app.js

$ pm2 start app.js -- -a 23  # Pass arguments '-a 23' argument to app.js script

$ pm2 start app.js --name serverone # Start a process and name it as serverone
                                    # you can now stop the process by doing
                                    # pm2 stop serverone

$ pm2 start app.js --node-args="--debug=7001" # --node-args to pass options to node V8

$ pm2 start app.js -i 0             # Start maximum processes depending on available CPUs (cluster mode)

$ pm2 start app.js --log-date-format "YYYY-MM-DD HH:mm Z"    # Log will be prefixed with custom time format

$ pm2 start app.json                # Start processes with options declared in app.json
                                    # Go to chapter Multi process JSON declaration for more

$ pm2 start app.js -e err.log -o out.log  # Start and specify error and out log
  
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
