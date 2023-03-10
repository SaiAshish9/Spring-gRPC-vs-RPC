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

Remote Procedure Call is a technique for building distributed systems. Basically, 
it allows a program on one machine to call a subroutine on another machine without
knowing that it is remote. RPC is not a transport protocol: rather, it is a method of
using existing communications features in a transparent way. This transparency is one 
of the great strengths of RPC as a tool. Because the application software does not 
contain any communication code, it is independent of
The particular communications hardware and protocols used
The operating system used
The calling sequence needed to use the underlying communications software
This means that application software can be designed and written before these choices 
have even been made. Because it takes care of any data reformatting needed, RPC also
provides transparency to byte ordering and differences in data representation (real 
number formats, etc). RPC is not a new technique.

https://www.javatpoint.com/what-is-rpc-in-operating-system

https://www.w3.org/History/1992/nfs_dxcern_mirror/rpc/doc/Introduction/WhatIs.html
#:~:text=Remote%20Procedure%20Call%20is%20a,features%20in%20a%20transparent%20way.

Its right now under CNCF(cloud native computing foundation) project for incubation.

gRPC is used by Netflix and Cisco.
```

```
gRPC is open source RPC framework that makes it easy to build a heterogenous distributed
system.

1. It's Free
2. Based on HTTP/2 today (multiplexed, works with internet) (trying to implement HTTP1)
3. Payload Agnostic (we've implemented proto)

gRPC use protcol buffers for communication.

Protocol buffers are Google’s language-neutral, platform-neutral, extensible mechanism 
for serializing structured data – think XML, but smaller, faster, and simpler. 
You define how you want your data to be structured once, then you can use special 
generated source code to easily write and read your structured data to and 
from a variety of data streams and using a variety of languages.

message Person {
  optional string name = 1;
  optional int32 id = 2;
  optional string email = 3;
}
A proto definition.

Languages supported by gRPC:

python, c/c++, ruby, java, go, c#, node.js, php.

protocol buffer is just another defination language. 

message Event {
   string topic = 1;
}

protocol buffer is a interface defination language (IDL). 
We'll define IDL in the same way we define protocol buffer 
schema.

It also has the data model which defines req and res structure

It used binary format for transmitting the requests.

Google Cloud Services provides protocol buffer support.

4. Streaming & Flow Controlled
5. Designed for harsh environments (timeout, lameducking,
load-balancing, cancellation, ...)
6. Support in 10 languages & first class mobile support
7. Layered & Pluggable - its bring own monitoring, auth, naming, load balancing, etc.
```

<img width="720" alt="Screenshot 2023-03-11 at 1 16 22 AM" src="https://user-images.githubusercontent.com/43849911/224413467-55314ce4-dfba-42e8-9b64-421822f0e25c.png">

<img width="736" alt="Screenshot 2023-03-11 at 1 16 38 AM" src="https://user-images.githubusercontent.com/43849911/224413505-d8579ba5-601e-4d1d-8d96-fa683ec4d18a.png">


```
Protocol Buffer Use Cases:
```

<img width="792" alt="Screenshot 2023-03-11 at 1 18 26 AM" src="https://user-images.githubusercontent.com/43849911/224413824-4e47e8cc-e4c2-4242-9e5d-4645f7fb9beb.png">

```
git clone -b v1.53.0 --depth 1 https://github.com/grpc/grpc-java
cd grpc-java/examples
./gradlew installDist

./build/install/examples/bin/hello-world-server

Mar 11, 2023 1:37:09 AM io.grpc.examples.helloworld.HelloWorldServer start
INFO: Server started, listening on 50051

./build/install/examples/bin/hello-world-client
Mar 11, 2023 1:37:15 AM io.grpc.examples.helloworld.HelloWorldClient greet
INFO: Will try to greet world ...
Mar 11, 2023 1:37:16 AM io.grpc.examples.helloworld.HelloWorldClient greet
INFO: Greeting: Hello world


cd src/main/proto/

ls
hello_streaming.proto	helloworld.proto	route_guide.proto

cat helloworld.proto 
// Copyright 2015 The gRPC Authors
//
// Licensed under the Apache License, Version 2.0 (the "License");
// you may not use this file except in compliance with the License.
// You may obtain a copy of the License at
//
//     http://www.apache.org/licenses/LICENSE-2.0
//
// Unless required by applicable law or agreed to in writing, software
// distributed under the License is distributed on an "AS IS" BASIS,
// WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
// See the License for the specific language governing permissions and
// limitations under the License.
syntax = "proto3";

option java_multiple_files = true;
option java_package = "io.grpc.examples.helloworld";
option java_outer_classname = "HelloWorldProto";
option objc_class_prefix = "HLW";

package helloworld;

// The greeting service definition.
service Greeter {
  // Sends a greeting
  rpc SayHello (HelloRequest) returns (HelloReply) {}
}

// The request message containing the user's name.
message HelloRequest {
  string name = 1;
}

// The response message containing the greetings
message HelloReply {
  string message = 1;
}

During the compile time new Greeter grpc will be created which has all 
the client of our classes based on definition. 
```

<img width="562" alt="Screenshot 2023-03-11 at 1 36 39 AM" src="https://user-images.githubusercontent.com/43849911/224417582-048538d7-5872-40cd-8492-674b667ec28d.png">

```
nano 
helloworld.proto 

cat helloworld.proto
// Copyright 2015 The gRPC Authors
//
// Licensed under the Apache License, Version 2.0 (the "License");
// you may not use this file except in compliance with the License.
// You may obtain a copy of the License at
//
//     http://www.apache.org/licenses/LICENSE-2.0
//
// Unless required by applicable law or agreed to in writing, software
// distributed under the License is distributed on an "AS IS" BASIS,
// WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
// See the License for the specific language governing permissions and
// limitations under the License.
syntax = "proto3";

option java_multiple_files = true;
option java_package = "io.grpc.examples.helloworld";
option java_outer_classname = "HelloWorldProto";
option objc_class_prefix = "HLW";

package helloworld;

// The greeting service definition.
service Greeter {
  // Sends a greeting
  rpc SayHello (HelloRequest) returns (HelloReply) {}
  rpc SayHelloAgain (HelloRequest) returns (HelloReply) {}
}

// The request message containing the user's name.
message HelloRequest {
  string name = 1;
}

// The response message containing the greetings
message HelloReply {
  string message = 1;
}


./gradlew installDist

nano src/main/java/io/grpc/examples/helloworld/HelloWorldServer.java

  @Override
  public void sayHelloAgain(HelloRequest req, StreamObserver<HelloReply> responseObserver) {
    HelloReply reply = HelloReply.newBuilder().setMessage("Hello again " + req.getName()).build();
    responseObserver.onNext(reply);
    responseObserver.onCompleted();
  }

ctrl x => yes

nano src/main/java/io/grpc/examples/helloworld/HelloWorldClient.java
ctrl x => yes

  try {
    response = blockingStub.sayHelloAgain(request);
  } catch (StatusRuntimeException e) {
    logger.log(Level.WARNING, "RPC failed: {0}", e.getStatus());
    return;
  }
  logger.info("Greeting: " + response.getMessage());

./gradlew installDist

./build/install/examples/bin/hello-world-server
Mar 11, 2023 2:04:36 AM io.grpc.examples.helloworld.HelloWorldServer start
INFO: Server started, listening on 50051


/build/install/examples/bin/hello-world-client                    
Mar 11, 2023 2:04:46 AM io.grpc.examples.helloworld.HelloWorldClient greet
INFO: Will try to greet world ...
Mar 11, 2023 2:04:46 AM io.grpc.examples.helloworld.HelloWorldClient greet
INFO: Greeting: Hello world
Mar 11, 2023 2:04:46 AM io.grpc.examples.helloworld.HelloWorldClient greet
INFO: Greeting: Hello again world

```

<img width="558" alt="Screenshot 2023-03-11 at 1 54 03 AM" src="https://user-images.githubusercontent.com/43849911/224421445-e6bb724a-14bf-4452-b251-3eeb68d6e3ba.png">

```
cat helloworld.proto 
// Copyright 2015 The gRPC Authors
//
// Licensed under the Apache License, Version 2.0 (the "License");
// you may not use this file except in compliance with the License.
// You may obtain a copy of the License at
//
//     http://www.apache.org/licenses/LICENSE-2.0
//
// Unless required by applicable law or agreed to in writing, software
// distributed under the License is distributed on an "AS IS" BASIS,
// WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
// See the License for the specific language governing permissions and
// limitations under the License.
syntax = "proto3";

option java_multiple_files = true;
option java_package = "io.grpc.examples.helloworld";
option java_outer_classname = "HelloWorldProto";
option objc_class_prefix = "HLW";

package helloworld;

// The greeting service definition.
service Greeter {
  // Sends a greeting
  rpc SayHello (HelloRequest) returns (HelloReply) {}
  rpc SayHelloAgain (HelloRequest) returns (HelloReply) {}
}

// The request message containing the user's name.
message HelloRequest {
  string name = 1;
}

// The response message containing the greetings
message HelloReply {
  string message = 1; 
}

default index as 1
```

<img width="985" alt="Screenshot 2023-03-11 at 1 57 36 AM" src="https://user-images.githubusercontent.com/43849911/224422006-43c3c883-16be-45f4-9e0c-b3a3ec39d5ae.png">

<img width="980" alt="Screenshot 2023-03-11 at 2 01 24 AM" src="https://user-images.githubusercontent.com/43849911/224422564-a967507d-c18d-4863-8998-b1ef93e97793.png">

<img width="983" alt="Screenshot 2023-03-11 at 2 04 05 AM" src="https://user-images.githubusercontent.com/43849911/224423021-eaedc62f-4904-4d64-ac99-37dbf672444f.png">

<img width="841" alt="Screenshot 2023-03-11 at 2 10 20 AM" src="https://user-images.githubusercontent.com/43849911/224424059-d1e7ea09-0477-42d7-967c-612ba690ddfe.png">

<img width="1122" alt="Screenshot 2023-03-11 at 2 17 15 AM" src="https://user-images.githubusercontent.com/43849911/224425196-649add04-a0fe-492b-91fb-c652661ff421.png">


```
proto buffs are basically the json schemas.
```
