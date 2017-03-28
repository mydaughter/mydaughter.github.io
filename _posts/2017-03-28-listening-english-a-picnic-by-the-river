---
layout: post
title:  "Socket.io: The necessity for beginners nodejs"
date:   2017-02-25 11:46:07
categories: tungns update
tags: nodejs javascript
image: /images/socket.io.png
description: "In this post, i will post some code helpful for beginners want to learn Socket.io"
author: "tungns"
---

Socket.IO is a JavaScript library for realtime web applications. It enables realtime, bi-directional communication between web clients and servers. It has two parts: a client-side library that runs in the browser, and a server-side library for Node.js. Both components have a nearly identical API. Like Node.js, it is event-driven.

In this post, i will post some code helpful for beginners want to learn NodeJs..

**1: Here is a nice little cheat sheet for sockets:**

``` javascript

// sending to sender-client only
socket.emit('message', "this is a test");

// sending to all clients, include sender
io.emit('message', "this is a test");

// sending to all clients except sender
socket.broadcast.emit('message', "this is a test");

// sending to all clients in 'game' room(channel) except sender
socket.broadcast.to('game').emit('message', 'nice game');

// sending to all clients in 'game' room(channel), include sender
io.in('game').emit('message', 'cool game');

// sending to sender client, only if they are in 'game' room(channel)
socket.to('game').emit('message', 'enjoy the game');

// sending to all clients in namespace 'myNamespace', include sender
io.of('myNamespace').emit('message', 'gg');

// sending to individual socketid
socket.broadcast.to(socketid).emit('message', 'for your eyes only');

```

**2: The number has connect to socket.io 
 In Socket.IO 1.4+

``` javascript

let numbers = Object.keys(io.sockets.connected);
console.log(numbers); // ex :4

```

**3: The number has in a channel**

``` javascript

    let rooms = self.io.sockets.adapter.rooms[channel];
    if(!rooms){
        return 0;
    }
    console.log(rooms.length);
    
```

**4: From server , socket can emit to multiple channel.

``` javascript

    io.sockets.to(channel1).to(channel2).emit('pushInfo', 'Hello! I'm TUngns');
    
```

** 5: In future , socket will provider a feature that's join multiple channel.
You can ref here: [https://github.com/socketio/socket.io/issues/2877](https://github.com/socketio/socket.io/issues/2877)

``` javascript

socket.join( 'channel01' ).join( 'channel02' );

```

P/s:
I could easily create my own private fork with this simple feature for my own personal usage, but wanted to see if there was more general interest in adding such a feature to the mainline.
Contact with me about that method if you want
skype: tungtrum17
email: nguyentung.main@gmail.com

Thanks a lot.
