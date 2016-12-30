---
layout: post
title:  "Meteor Js - : How to set different port on Meteor."
date:   2016-12-31 19:24:00
categories: admin post
tags: meteor javascript nodejs js
image: /images/imgMeteor.png
description: "Meteor is a complete platform for building web and mobile apps in pure JavaScript... So How to start Meteor on different port.."
author: "Admin"
---
Meteor is a complete platform for building web and mobile apps in pure JavaScript... 


## So How to start Meteor on different port..

#### install Meteor :

{% highlight html %}

$ curl https://install.meteor.com/ | sh


{% endhighlight %}

When install meteor completely then default Meteor app will start on port 3000:


{% highlight html %}

$ meteor
[[[[[ ~/Documents/ALL/QUEENB/PROJECTS/METEORJS/book-list ]]]]]

=> Started proxy.                             
=> Started MongoDB.                           
=> Started your app.                          

=> App running at: http://localhost:3000/


{% endhighlight %}


## Now, we want change Meteor Port 3002:

To start Meteor on a different port , then we'll start Meteor with --port parameter:

{% highlight html %}

$ meteor --port 3002
[[[[[ ~/Documents/ALL/QUEENB/PROJECTS/METEORJS/book-list ]]]]]

=> Started proxy.                             
=> Started MongoDB.                           
=> Started your app.                          

=> App running at: http://localhost:3002/

{% endhighlight %}

# NOTE: For port lower than 1024, need `sudo`

{% highlight html %}

$ meteor --port 80
Error: listen EACCES


$ sudo meteor --port 80
[[[[[ ~/Documents/ALL/QUEENB/PROJECTS/METEORJS/book-list ]]]]]

=> Started proxy.                             
=> Started MongoDB.                           
=> Started your app.                          

=> App running at: http://localhost:80/

{% endhighlight %}

