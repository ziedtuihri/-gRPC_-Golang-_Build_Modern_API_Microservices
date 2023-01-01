# -gRPC_-Golang-_Build_Modern_API_Microservices

<h3> Internals Deep Dive </h3>

Protocol Buffers role in gRPC

Protocol Buffers is used to define the: 

Messages(data, Request and Response)

Service (Service name and RPC endpoints)

we then generate code from it! 

gRPC uses Protocol Buffers for communications.

Let's measure the payload size vs JSON

JSON 55 bytes same in Protocol Buffers: 20 bytes

we save in Network Bandwidth

Parsing JSON is actually CPU intensive (because the format is human readable)

Parsing Protocol Buffers (binary format) is less CPU intensive because it's closer to how a machine represents data

By using gRPC the use of Protocol Buffers means faster and more efficient communication, friendly with mobile devices that have a slower CPU

<pre>gRPC will have the main implementations:
  gRPC-JAVA pure implementation of gRPC in java
  gRPC-Go pure implementation of gRPC in Go
  gRPC-C pure implementation of gRPC in C
    gRPC C++
    gRPC Python
    gRPC Ruby
    gRPC Objective C
    gRPC PHP
    gRPC C#</pre>
    
```diff
+  one of the biggest benefits is often overlooked: multi-language support.
```    
 gRPC can be use by any language
because the code can be generated for any language, it makes it super simple to create micro-services in any language that interact with each other

gRPC leverages HHTP/2 as a backbone for communications
<a hrf="https://imagekit.io/demo/http2-vs-http1">https://imagekit.io/demo/http2-vs-http1</a>
<h3>3.1 HTTP2 vs HTTP1 comparison</h3>
HTTP 1.1 apons a new TCP connection to a server at each request it does not copress headers (which are plaintext)
it only works with Request / Response mechanism (no serve push)

HTTP was originally composed of two commands:
GET: to ask for content
POST: to send content
HOW HTTP/1.1 works 
each request opnes a TCP connection these inefficiencies add latency and increase network packet size
HTTP 2 was released in2015 (and was before that tested by Google under the name SPDY)

HTTP 2 supports multiplexing
The client & server can push messages in parallel over the same TCP connection this greatly reduces latency
HTTP 2 support server push servers can push streams(multiple messages) for one request from the client this saves round trips (latency)
HTTP 2 supports header compression 
Headers (text based) can now be compressed
These have much less impact on the packet size
remember the average http request may have over 20 headers due to cookies content cache and application headers
HTTP 2 is binary
while HTTP/1 text makes it easy for debugging it's not efficient over the network (protocol buffers is a binary protocol and makes it a great match for HTTP2)

HTTP/2 is secure (SSL is not required but recommended by default)





  


