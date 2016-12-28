---
layout: post
title:  "NodeJs: Hello World cho người bắt đầu tìm hiểu Nodejs "
date:   2016-12-27 11:46:07
categories: tungns update
tags: helloworld node cache
image: /images/nodejshelloworld.png
description: "NodeJs: Hello World cho người bắt đầu tìm hiểu Nodejs. Như các bạn đã biết thì hầu hết các ngôn ngữ trên thế giới đều có các demo kinh điển đó là 'Hello World'
Ở bài học này chúng ta sẽ làm một demo như vậy để thấy Nodejs nó được hoạt động như thế nào. Vậy chúng ta cần bắt đầu nào."
author: "tungns"
---
Như các bạn đã biết thì hầu hết các ngôn ngữ trên thế giới đều có các demo kinh điển đó là *Hello World*. 
Ở bài học này chúng ta sẽ làm một demo như vậy để thấy Nodejs nó được hoạt động như thế nào. Vậy chúng ta cần bắt đầu nào.


Việc đầu tiên ở đây là khi install node thì nodejs hỗ trợ nhiều hệ điều hành khác nhau , nhưng ở đây Linux và OSX được khuyến khích, nhưng bạn cũng có thể sử dụng FreeBSD và Cygwin (trên Window).
Cách phổ biến nhất để cài đặt Node.js là để trực tiếp biên dịch nó từ mã nguồn đã tải. Ngoài ra còn có các gói khác nhau có sẵn cho các nhà quản lý các gói khác nhau, nhưng vì tần số cập nhật của họ khác nhau, tôi khuyên bạn nên cài đặt từ mã nguồn này.
Bạn có thể lấy mã nguồn mới nhất từ [nodejs.org](https://nodejs.org). Và chạy những câu lệnh dưới đây.


{% highlight javascript %}

$ wget https://nodejs.org/dist/node-v6.9.2.tar.gz
$ tar -xzf node-v6.9.2.tar.gz
$ cd node-v6.9.2
$ ./configure
$ sudo make install

{% endhighlight %}

Node.js tự nó không có phụ thuộc bên ngoài ngoại trừ các công cụ xây dựng thông thường cũng như trăn cho việc xây dựng hệ thống chính nó. Ngày OSX bạn phải cài đặt XCode để làm việc này, và trên Ubuntu bạn có thể có để chạy:

{% highlight javascript %}

$ apt-get -y install build-essential

{% endhighlight %}

Sau khi install câu lệnh trên bạn có thể thử như câu lệnh dưới đây. Nếu bạn giống như thế này thì trước tiên bạn đã thành công trong việc install nodejs.


{% highlight javascript %}

$ node
> console.log('Hello World');
Hello World

{% endhighlight %}

## Chương trình đầu tiên :
Trước tiên các bạn tạo Folder cho các bạn. Ví dụ tôi có folder: */projects/HelloWorldForNodejs*
Sau đó các bạn tạo file server.js hay name gì đó tuỳ các bạn. Nhưng nhớ là phần mở rộng là .js. Sau khi tao xong tôi tao thêm code vào file này thì file server.js sẽ có như thế này .


{% highlight javascript %}

var http = require('http');

var server = http.createServer(function(req, res) {
  res.writeHead(200);
  res.end('Hello World ');
});
server.listen(8080);

{% endhighlight %}

Tiếp đến chạy lệnh như thế này :


{% highlight javascript %}

$ node server.js

{% endhighlight %}


Vậy là xem như xong , giờ chúng ta muốn chạy nó  với port 8080 thì mở browser lên và run *http://localhost:8080*
Như vậy chúng ta có một site với nội dung là  `Hello World ` ... Đương nhiên nó chạy port 8080. Chúng ta có thể thay đổi port đó tuỳ mỗi người nhé..
Xong rồi đó, qua bài này các bạn có thể thấy được và hình dung việc install và run NodeJs như thế nào.. Chúc các bạn thành công! 
