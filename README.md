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



