---
layout: post
title:  "NODEJS - :Đường dẫn tuyệt đối và require() trong nodejs"
date:   2016-12-28 19:24:00
categories: mailam update
tags: nodejs require paths
image: /images/pathrequire.png
description: "Có nhiều lúc chúng ta xây dựng nhiều folder trong một project nodejs. Nhưng khi sử dụng require() thì chúng ta lại lúng túng trong việc dẫn đường path vào. Vậy cho nên trong bài này tôi có một cách mà tôi vô tình lướt qua trên Google... Các bạn xem nhé."
author: "Mai Lam"
---
Có nhiều lúc chúng ta xây dựng nhiều folder trong một project nodejs. Nhưng khi sử dụng require() thì chúng ta lại lúng túng trong việc dẫn đường path vào. Vậy cho nên trong bài này tôi có một cách mà tôi vô tình lướt qua trên Google... Các bạn xem nhé.

Để tôi ví dụ: 


{% highlight html %}

var a = require('./config/Util.js');
var b = require('././config/Util.js');

{% endhighlight %}


Đấy các bạn thấy không, Chỉ có một cái đúng thôi đấy... Nhưng chúng ta vẫn có thể nhầm lẫn điều đó. Vậy phải làm thế nào để path đó chắc chắc là đúng... Hehe Giải pháp như sau. Ví dụ tôi có  :

### app.js


{% highlight html %}

global.base_dir = __dirname;
global.abs_path = function(path) {
  return base_dir + path;
}
global.include = function(file) {
  return require(abs_path('/' + file));
}

{% endhighlight %}


### How to use it :

Thay vì lúc trước chúng ta viết :

{% highlight html %}

require('../../../lib/Utils.js');

{% endhighlight %}

Thì bây giờ nó sẽ là :


{% highlight html %}

include('lib/Utils.js');

{% endhighlight %}


Chúng ta không còn quan tâm đến những ../ ở trước nữa đúng không. Vậy là xong .. pp.
