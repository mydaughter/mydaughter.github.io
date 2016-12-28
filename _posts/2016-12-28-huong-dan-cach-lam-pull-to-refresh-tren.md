---
layout: post
title:  "HTML5 And JS: Hướng dẫn cách làm Pull To Refresh trên website."
date:   2016-12-28 19:24:00
categories: mailam update
tags: pulltorefresh html5 js
image: /images/pulltorefresh.png
description: "Pull to refresh tạm dịch là 'Kéo để làm mới trang' là một chức năng rất hay trên các thiết bị iOS và trên Android. Hôm nay, mình giới thiệu một plugin nhỏ để tạo hiệu ứng này trên website. Plugin này mang tên Hook.js dung lượng chỉ khoảng 15KB."
author: "mailam"
---
Pull to refresh tạm dịch là *Kéo để làm mới trang* là một chức năng rất hay trên các thiết bị iOS và trên Android. Hôm nay, mình giới thiệu một plugin nhỏ để tạo hiệu ứng này trên website. Plugin này mang tên Hook.js dung lượng chỉ khoảng 15KB.

Vì dung lượng nhỏ cho nên nó sẽ không làm ảnh hưởng gì tới website của bạn. Bạn có thể Download plugin Hook tại đây: [Download hookjs](http://www.jqueryscript.net/download/jQuery-Pull-to-Refresh-Plugin-for-Web-Page-Hook-js.zip). Sau đó add thêm những code dưới đây vào website của bạn.


{% highlight html %}

<script src="http://code.jquery.com/jquery-latest.js" type="text/javascript"></script>
<link rel="stylesheet" href="hook/hook.css" type="text/css" />
<script src="hook/hook.js" type="text/javascript"></script>

{% endhighlight %}


Và trong thẻ <body> các bạn thêm thẻ <div> như thế này...


{% highlight html %}

<div id="hook">
    <div id="loader">
        <div class="spinner"></div>
    </div>
    <span id="hook-text">Reloading...</span>
</div>

{% endhighlight %}


Như vậy chúng ta đã có một cách refresh như các thiết bị mobile. ^^ . Qua đây chúng ta có thể thấy được rất nhiều công nghệ của mobile đã có trên webiste nhé các bạn. 
