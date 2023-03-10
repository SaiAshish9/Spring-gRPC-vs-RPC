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

Remote Procedure Call is a technique for building distributed systems. Basically, it allows a program on one machine to call a subroutine on another machine without knowing that it is remote. RPC is not a transport protocol: rather, it is a method of using existing communications features in a transparent way. This transparency is one of the great strengths of RPC as a tool. Because the application software does not contain any communication code, it is independent of
The particular communications hardware and protocols used
The operating system used
The calling sequence needed to use the underlying communications software
This means that application software can be designed and written before these choices have even been made. Because it takes care of any data reformatting needed, RPC also provides transparency to byte ordering and differences in data representation (real number formats, etc). RPC is not a new technique.

https://www.w3.org/History/1992/nfs_dxcern_mirror/rpc/doc/Introduction/WhatIs.html#:~:text=Remote%20Procedure%20Call%20is%20a,features%20in%20a%20transparent%20way.

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
