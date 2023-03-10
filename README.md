```
Google Remote Procedure Call (gRPC) is roughly 7 times faster than REST when receiving 
data & roughly 10 times faster than REST when sending data for this specific payload. 
This is mainly due to the tight packing of the Protocol Buffers and
the use of HTTP/2 by gRPC

gRPC is a modern open source high performance Remote Procedure Call 
(RPC) framework that can run in any environment. It can efficiently 
connect services in and across data centers with pluggable support 
for load balancing, tracing, health checking and authentication. 
It is also applicable in last mile of distributed computing to 
connect devices, mobile applications and browsers to backend services.

Google Remote Procedure Call, more commonly known as gRPC,
is a remote procedure call (RPC) framework that brings
performance benefits and modern features to client-server 
applications. Like RPC, it allows you to directly 
call methods on other machines.

Its right now under CNCF(cloud native computing foundation) project for incubation.

gRPC is used by Netflix and Cisco.
```

```
gRPC is open source RPC framework that makes it easy to build a heterogenous distributed
system.

1. It's Free
2. Based on HTTP/2 today (multiplexed, works with internet) (trying to implement HTTP1)
3. Payload Agnostic (we've implemented proto)
4. Streaming & Flow Controlled
5. Designed for harsh environments (timeout, lameducking,
load-balancing, cancellation, ...)
6. Support in 10 languages & first class mobile support
7. Layered & Pluggable - its bring own monitoring, auth, naming, load balancing, etc.
```
