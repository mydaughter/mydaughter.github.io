---
layout: post
title:  "Tutorial: Working with Node.js and Redis"
date:   2016-12-09 11:46:07
categories: tungns update
tags: tungns update
image: /images/pic01.jpg
---
Create a new folder and put a new text file in it called: * app.js *

Inside the app.js file we will add some simple code to set a value that doesn’t have a time to live (or expiration on it):

{% highlight javascript %}
var redis = require("redis")
    , client = redis.createClient();
 
client.on("error", function (err) {
    console.log("Error " + err);
});
 
client.on("connect", runSample);
 
function runSample() {
    // Set a value
    client.set("string key", "Hello World", function (err, reply) {
        console.log(reply.toString());
    });
    // Get a value
    client.get("string key", function (err, reply) {
        console.log(reply.toString());
    });
}
{% endhighlight %}



When we connect to Redis and everything is ready the runSample function is called which in turn sets a value and then reads it back.

Expected output:

{% highlight javascript %}
OK
Hello World

{% endhighlight %}
