# TCP/IP/XDCC/WebSockets

## Learning Competencies
- Learning TCP/IP
- XDCC communication
- WebSockets with Node.js

## Overview

### (TCP/IP) Introduction to Concepts
#### Wiki Says
> The Transmission Control Protocol (TCP) is one of the main protocols of the Internet protocol suite. It originated in the initial network implementation in which it complemented the Internet Protocol (IP). Therefore, the entire suite is commonly referred to as TCP/IP. TCP provides reliable, ordered, and error-checked delivery of a stream of octets between applications running on hosts communicating by an IP network. Major Internet applications such as the World Wide Web, email, remote administration, and file transfer rely on TCP. Applications that do not require reliable data stream service may use the User Datagram Protocol (UDP), which provides a connectionless datagram service that emphasizes reduced latency over reliability. Follow [Wiki](https://en.wikipedia.org/wiki/Transmission_Control_Protocol) for more. 


#### Below is entire Computer Networking Playlist. Learn anything that you don't. Especially TCP/IP

[![Eli the Computer guy](imgs/eli.png)](https://www.youtube.com/playlist?list=PLF360ED1082F6F2A5)


#### What is TCP?
Transmission Control Protocol(TCP) is a connection-oriented protocol that provides reliable and ordered delivery of data from one computer to another.

In other words, TCP is the transport protocol you use whenever you want to ensure that all the bytes you send from one point reach the other completely and in the correct order.

For these and other reasons, most protocols that you use now, such as HTTP, are built on top of TCP. When you send the HTML for a page, you want it to get to the other end in the exact form that you sent it,
and if that is not possible, an error should be triggered. If even one character (byte) of the stream were to be misplaced, a browser might not be able to render the page.

Node.JS is a framework designed with the development of networked applications in mind. Today, applications in a network communicate over the transport known as TCP/IP. Therefore it’s crucial that we have an understanding about how TCP/IP basically works, and how Node.JS expresses it with its amazingly simple APIs.

#### What are the characteristics of TCP?
- Connection-oriented communication and same-order delivery
- Byte Orientation
- Reliability
- Flow Control
- Congestion Control 

#### What is IP?
Internet Protocol (IP) is the principal set (or communications protocol) of digital message formats and rules for exchanging messages between computers across a single network or a series of interconnected networks, using the Internet Protocol Suite (often referred to as TCP/IP). Messages are exchanged as datagrams, also known as data packets or just packets.
#### Analogy
Think of an anology with the postal system. IP is similar to the Indian Postal System in that it allows a package (a datagram) to be addressed (encapsulation) and put into the system (the Internet) by the sender (source host). However, there is no direct link between sender and receiver. 

The package (datagram) is almost always divided into pieces, but each piece contains the address of the receiver (destination host). Eventually, each piece arrives at the receiver, often by different routes and at different times. These routes and times are also determined by the Postal System, which is the IP. However, the Postal System (in the transport and application layers) puts all the pieces back together before delivery to the receiver (destination host).

You may read all about this in detail in the book **Smashing Node.js**

### (XDCC) Introduction to Concepts

#### Wiki Says
> XDCC (Xabi DCC or eXtended DCC) is a computer file sharing method which uses the Internet Relay Chat (IRC) network as a host service. Follow [Wiki](https://en.wikipedia.org/wiki/XDCC) for more. 

#### Let's start with IRC
Internet Relay Chat (IRC) is a system for chatting that involves a set of rules and conventions and client/server software. On the Web, certain sites such as Talk City or IRC networks such as the Undernet provide servers and help you download an IRC client to your PC.

#### What is XDCC?

In order to understand the basics of XDCC we first need to understand DCC in general. DCC stands for Direct Client-to-Client, it is a way to establish a “communication” between clients, in this case the clients being the IRC clients. DCC is not a standard, neither is XDCC. DCC is an extension added by the IRC clients in order to facilitate the sending of files via IRC. IRC in itself does not support DCC, when you are sending a file or opening a DCC chat it goes straight from your computer to the target computer, hence the “Direct”.

### (WebSockets) Introduction to Concepts


#### [Difference b/w Websockets & Socket.IO in Node.js]()

So far, most website and web application developers are accustomed to communicating exclusively with a server by making HTTP requests that are followed by HTTP responses.

The model of *requesting a resource* by specifying its URL, `Content-Type`, and other attributes that you saw in previous chapters works well if you keep in mind the use case that the World Wide Web was crafted to solve. The web was created to deliver documents that were heavily interlinked to each other.

URLs have paths because documents typically have hierarchies in file systems. And each level of hierarchy can contain indexes with hyperlinks.
Consider the following, for example:
```
GET /animals/index.html
GET /animals/mammals/index.html
GET /animals/mammals/ferrets.html
```
With time, however, the web became more and more interactive. The traditional web that was about retrieving entire documents every time the user clicked is less common nowadays, especially with all the tools that HTML5 makes available. You can now create very sophisticated web applications that often have completely deprecated desktop application counterparts, games, text editors, and more.

#### Wiki Says
> WebSocket is a computer communications protocol, providing full-duplex communication channels over a single TCP connection. The WebSocket protocol was standardized by the IETF as RFC 6455 in 2011, and the WebSocket API in Web IDL is being standardized by the W3C.
> WebSocket is designed to be implemented in web browsers and web servers, but it can be used by any client or server application. The WebSocket Protocol is an independent TCP-based protocol. Its only relationship to HTTP is that its handshake is interpreted by HTTP servers as an Upgrade request. The WebSocket protocol enables interaction between a browser and a web server with lower overheads, facilitating real-time data transfer from and to the server. This is made possible by providing a standardized way for the server to send content to the browser without being solicited by the client, and allowing for messages to be passed back and forth while keeping the connection open. In this way, a two-way (bi-directional) ongoing conversation can take place between a browser and the server. The communications are done over TCP port number 80 (or 443 in the case of TLS-encrypted connections), which is of benefit for those environments which block non-web Internet connections using a firewall. Similar two-way browser-server communications have been achieved in non-standardized ways using stopgap technologies such as Comet.
> The WebSocket protocol is currently supported in most major browsers including Google Chrome, Microsoft Edge, Internet Explorer, Firefox, Safari and Opera. WebSocket also requires web applications on the server to support it.

#### What is WebSocket?

WebSocket is a protocol which allows for communication between the client and the server/endpoint using a single TCP connection. Sounds a bit like http doesn’t it? The advantage WebSocket has over HTTP is that the protocol is full-duplex (allows for simultaneous two-way communcation) and it’s header is much smaller than that of a HTTP header, allowing for more efficient communcation even over small packets of data.

The life cycle of a WebSocket is easy to understand as well:

1. Client sends the Server a handshake request in the form of a HTTP upgrade header with data about the WebSocket it’s attempting to connect to.

2. The Server responds to the request with another HTTP header, this is the last time a HTTP header gets used in the WebSocket connection. If the handshake was successful, they server sends a HTTP header telling the client it’s switching to the WebSocket protocol.

3. Now a constant connection is opened and the client and server can send any number of messages to each other until the connection is closed. These messages only have about 2 bytes of overhead.

#### SOCKET.IO
Socket.IO enables real-time bidirectional event-based communication. It works on every platform, browser or device, focusing equally on reliability and speed. Socket.IO is built on top of the WebSockets API(Client side) and Node.js. It is one of the most depended-upon library on npm.

#### Code Along

Let's create a file called app.js and enter the following to set up an express application:
```js
var app = require('express')();
var http = require('http').Server(app);

app.get('/', function(req, res){
  res.sendfile('index.html');
});

http.listen(3000, function(){
  console.log('listening on *:3000');
});
```
We'll need an index.html file to serve, create a new file called index.html and enter the following in it:
```html
<!DOCTYPE html>
<html>
  <head><title>Hello world</title></head>
  <body>Hello world</body>
</html>
```
To test if this works, go to your terminal and run this app using
```
nodemon app.js
```
This will run your server on localhost:3000. Go to your browser and enter `localhost:3000` to check this.

This set up our express application and is now serving a HTML file on the root route. Now we will require socket.IO and will log "A user connected", everytime a user goes to this page and "A user disconnected", everytime someone navigates away/closes this page.
```js
var app = require('express')();
var http = require('http').Server(app);
var io = require('socket.io')(http);

app.get('/', function(req, res){
  res.sendfile('index.html');
});

//Whenever someone connects this gets executed
io.on('connection', function(socket){
  console.log('A user connected');

  //Whenever someone disconnects this piece of code executed
  socket.on('disconnect', function () {
    console.log('A user disconnected');
  });

});

http.listen(3000, function(){
  console.log('listening on *:3000');
});
```
The require('socket.io')(http) creates a new socket.io instance attached to the http server. The io.on event handler handles connection, disconnection, etc events in it, using the socket object.

We have set uo our server to log messages on connections and disconnections. Now also need to include the client script and initialize the socket object there so that clients can establish connections when required. The script is served by our io server at '/socket.io/socket.io.js'. After doing the above, the index.html file will look like:

```html
<!DOCTYPE html>
<html>
  <head><title>Hello world</title></head>
  <script src="/socket.io/socket.io.js"></script>
  <script>
    var socket = io();
  </script>
  <body>Hello world</body>
</html>
```
If you go to `localhost:3000` now(make sure your server is running), you'll get Hello world printed in your browser. Now check your server console logs, it'll show a message:
```
A user connected
```
If you refresh your browser, it'll disconnect the socket connection and recreate. You can see this on your console logs:
```
A user connected
A user disconnected
A user connected
```
We now have socket connections working. This is how easy it is to set up connections in socket.IO.

## Exploration
- Check out [this](http://searchnetworking.techtarget.com/definition/TCP-IP) article on **TCP/IP** by *Margaret Rouse*
- You may look at the [code](https://gist.github.com/creationix/707146) describing *A simple TCP chat server in node.js*.
- Read [this](http://blog.aeguana.com/2015/01/10/xdcc-tutorial/) blog by *The Akatsuki*.
- Check out [this](http://theloadguru.com/xdcc-irc-beginners-guide/) website on **XDCC IRC Beginners Guide** by *The Main Guru*. 
- Check out [this](https://www.youtube.com/watch?v=FlJ9SuZJy6w) video on XDCC.
- Read [this](http://blog.teamtreehouse.com/an-introduction-to-websockets) blog **An Introduction to WebSockets** by *Matt West*
- Read [this](https://code.tutsplus.com/tutorials/start-using-html5-websockets-today--net-13270) tutorial on **Websockets** by *Umar Hansa*.
- Check out *Socket.io* [documentation](https://socket.io/docs/).
- Chek out [this](https://stackoverflow.com/questions/16945345/differences-between-tcp-sockets-and-web-sockets-one-more-time) *StackOverFlow* link explaining the differences between a TCP & a websocket.
