---
layout: post
title:  "NodeJs: Hello World cho người bắt đầu tìm hiểu Nodejs "
date:   2016-12-27 11:46:07
categories: tungns update
tags: helloworld node cache
image: /images/nodejshelloworld.png
---
Như các bạn đã biết thì hầu hết các ngôn ngữ trên thế giới đều có các demo kinh điển đó là *Hello World*. 
Ở bài học này chúng ta sẽ làm một demo như vậy để thấy Nodejs nó được hoạt động như thế nào. Vậy chúng ta cần bắt đầu nào ...
{% highlight javascript %}
var redis = require("redis")
    , client = redis.createClient();
 
client.on("error", function (err) {
    console.log("Error " + err);
});
 
client.on("connect", runSample);
 
function runSample() {
    // Set a value
    client.set("string key", "Hello My Daughter", function (err, reply) {
        console.log(reply.toString());
    });
    // Get a value
    client.get("string key", function (err, reply) {
        console.log(reply.toString());
    });
}
{% endhighlight %}



Khi tôi kết nối với Redis và tất cả mọi thứ đã sẵn sàng các chức năng runSample được gọi lần lượt đặt một giá trị và sau đó đọc nó trở lại.

Kết quả xuất ra : 

{% highlight javascript %}
OK
Hello My Daughter

{% endhighlight %}

Và bây giờ tôi thêm một ví dụ về thời hạn của key này:

{% highlight javascript %}

var redis = require('redis')
    , client = redis.createClient();
 
client.on('error', function (err) {
    console.log('Error ' + err);
});
 
client.on('connect', runSample);
 
function runSample() {
    // Set a value with an expiration
    client.set('string key', 'Hello World', redis.print);
    // Expire in 3 seconds
    client.expire('string key', 3);
 
    // This timer is only to demo the TTL
    // Runs every second until the timeout
    // occurs on the value
    var myTimer = setInterval(function() {
        client.get('string key', function (err, reply) {
            if(reply) {
                console.log('I live: ' + reply.toString());
            } else {
                clearTimeout(myTimer);
                console.log('I expired');
                client.quit();
            }
        });
    }, 1000);
}

{% endhighlight %}
Rồi các bạn thấy đấy nó sẽ hiện ra như thế này.Sau khi 3 giây đi qua thì nó hết hạn. 
{% highlight javascript %}
Reply: OK
I live: Hello World
I live: Hello World
I live: Hello World
I expired
{% endhighlight %}

Bây giờ tôi sẽ kiểm tra xem có bao nhiêu thời gian một giá trị đã để lại trước khi nó hết hạn:

{% highlight javascript %}
var redis = require('redis')
    , client = redis.createClient();
 
client.on('error', function (err) {
    console.log('Error ' + err);
});
 
client.on('connect', runSample);
 
function runSample() {
    // Set a value
    client.set('string key', 'Hello World', redis.print);
    // Expire in 3 seconds
    client.expire('string key', 3);
 
    // This timer is only to demo the TTL
    // Runs every second until the timeout
    // occurs on the value
    var myTimer = setInterval(function() {
        client.get('string key', function (err, reply) {
            if(reply) {
                console.log('I live: ' + reply.toString());
                client.ttl('string key', writeTTL);
            } else {
                clearTimeout(myTimer);
                console.log('I expired');
                client.quit();
            }
        });
    }, 1000);
}
 
function writeTTL(err, data) {
    console.log('I live for this long yet: ' + data);
}
{% endhighlight %}

Chạy chương trình và kết quả như sau : 

{% highlight javascript %}
Reply: OK
I live: Hello World
I live for this long yet: 2
I live: Hello World
I live for this long yet: 1
I live: Hello World
I live for this long yet: 0
I expired
{% endhighlight %}

Remove all users : commend :redis-cli flushall


{% highlight javascript %}
var user_rahul = { 
    username: 'tungns'
};
var user_namita = {
    username: 'mailam'
};
client.hset('users', "123", JSON.stringify(user_rahul));
client.hset('users', "456", JSON.stringify(user_namita));

//get all users 
client.hgetall("users" , function(err, user) {
    console.log("user---",user);
});

//get single user have id is 123
client.hget("users", '123', function(err, user) {
    console.log("user--123-",user);
});

{% endhighlight %}
