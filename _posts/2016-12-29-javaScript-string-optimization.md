---
layout: post
title:  "JavaScript -: JavaScript String optimization"
date:   2016-12-29 19:24:00
categories: mailam update
tags: OPTIMIZATION JAVASCRIPT
image: /images/imgJavascript.png
description: "JavaScript String optimization"
author: "coderwall.com"
---
JavaScript String optimization.

JavaScript String optimization


{% highlight html %}

String.prototype.equals = function(value) {
    return this.valueOf() === value.valueOf();
}

String.prototype.endsWith = function(value) {
    return this.indexOf(suffix, this.length - value.length)  !== -1;
}

String.prototype.startsWith = function(value) {
    return this.indexOf(value) === 0;
}

String.prototype.isEmail = function() {
    re = /^((([a-z]|\d|[!#\$%&'\*\+\-\/=\?\^_`{\|}~]|[\u00A0-\uD7FF\uF900-\uFDCF\uFDF0-\uFFEF])+(\.([a-z]|\d|[!#\$%&'\*\+\-\/=\?\^_`{\|}~]|[\u00A0-\uD7FF\uF900-\uFDCF\uFDF0-\uFFEF])+)*)|((\x22)((((\x20|\x09)*(\x0d\x0a))?(\x20|\x09)+)?(([\x01-\x08\x0b\x0c\x0e-\x1f\x7f]|\x21|[\x23-\x5b]|[\x5d-\x7e]|[\u00A0-\uD7FF\uF900-\uFDCF\uFDF0-\uFFEF])|(\\([\x01-\x09\x0b\x0c\x0d-\x7f]|[\u00A0-\uD7FF\uF900-\uFDCF\uFDF0-\uFFEF]))))*(((\x20|\x09)*(\x0d\x0a))?(\x20|\x09)+)?(\x22)))@((([a-z]|\d|[\u00A0-\uD7FF\uF900-\uFDCF\uFDF0-\uFFEF])|(([a-z]|\d|[\u00A0-\uD7FF\uF900-\uFDCF\uFDF0-\uFFEF])([a-z]|\d|-|\.|_|~|[\u00A0-\uD7FF\uF900-\uFDCF\uFDF0-\uFFEF])*([a-z]|\d|[\u00A0-\uD7FF\uF900-\uFDCF\uFDF0-\uFFEF])))\.)+(([a-z]|[\u00A0-\uD7FF\uF900-\uFDCF\uFDF0-\uFFEF])|(([a-z]|[\u00A0-\uD7FF\uF900-\uFDCF\uFDF0-\uFFEF])([a-z]|\d|-|\.|_|~|[\u00A0-\uD7FF\uF900-\uFDCF\uFDF0-\uFFEF])*([a-z]|[\u00A0-\uD7FF\uF900-\uFDCF\uFDF0-\uFFEF])))\.?$/;
    return re.test(this);
}

String.prototype.ucfirst = function(value) {
    return this.charAt(0).toUpperCase() + this.slice(1)
}

String.prototype.crop = function(size, pattern) {
    if (pattern === undefined) 
        pattern = ' ... ';

    if (this.length <= size)
        return this;

    s = Math.floor((size - pattern.length) / 2);
    return this.substr(0, s) + pattern + this.substr(this.length - s, s)
}


String.prototype.trim = function() { 
    return this.replace(/^\s+/g,'').replace(/\s+$/g,'');
}

{% endhighlight %}


### Usage:


{% highlight html %}

'mailam'.equals('bar') // FALSE
'lorem ipsum'.endsWith('ipsum') // TRUE
'lorem ipsum'.startsWith('ipsum') // FALSE
'example@email.com'.isEmail() // TRUE
'example.com'.isEmail() // FALSE
'example@email'.isEmail() // FALSE
'mailam'.ucfirst() // Mailam
'Lorem ipsum dolor sit amet, consectetur adipisicing elit'.crop(25) // Lorem ipsu ... sicing elit

{% endhighlight %}


