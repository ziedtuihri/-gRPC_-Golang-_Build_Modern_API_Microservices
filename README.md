# -gRPC_-Golang-_Build_Modern_API_Microservices

<h3> 2. Protocol Buffers & Language Interoperability </h3>

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
<h3>3 HTTP2 vs HTTP1 comparison</h3>
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

<h3>3) Protoc Setup </h3><br>
In order to perform code generation, you will need to install protoc  on your computer.

============ MacOSX =============

It is actually very easy, open a command line interface and type brew install protobuf 

============ Ubuntu (Linux) ============

Find the correct protocol buffers version based on your Linux Distro: https://github.com/google/protobuf/releases

Example with x64:

<h3> Make sure you grab the latest version </h3>
curl -OL https://github.com/google/protobuf/releases/download/v3.5.1/protoc-3.5.1-linux-x86_64.zip
<h3> Unzip </h3>
unzip protoc-3.5.1-linux-x86_64.zip -d protoc3
<h3>  Move protoc to /usr/local/bin/ </h3>
sudo mv protoc3/bin/* /usr/local/bin/
<h3>  Move protoc3/include to /usr/local/include/ </h3>
sudo mv protoc3/include/* /usr/local/include/
<h3>  Optional: change owner </h3>
sudo chown [user] /usr/local/bin/protoc
sudo chown -R [user] /usr/local/include/google
============ Windows ============

Download the windows archive: https://github.com/google/protobuf/releases

Example: https://github.com/google/protobuf/releases/download/v3.5.1/protoc-3.5.1-win32.zip

Extract all to C:\proto3  

Your directory structure should now be

C:\proto3\bin 

C:\proto3\include 

Finally, add C:\proto3\bin to your PATH:

From the desktop, right-click My Computer and click Properties.
In the System Properties window, click on the Advanced tab
In the Advanced section, click the Environment Variables button.
Finally, in the Environment Variables window (as shown below), highlight the Path variable in the Systems Variable section and click the Edit button. Add or modify the path lines with the paths you wish the computer to access. Each different directory is separated with a semicolon as shown below.

C:\Program Files; C:\Winnt; ...... ; C:\proto3\bin
(you need to add ; C:\proto3\bin  at the end)





  


