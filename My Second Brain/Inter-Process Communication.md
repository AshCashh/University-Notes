---
tags: [cs, os]
Created: 2023-08-05T23:37:23+10:00
Modified: 2024-07-03T19:35:33+10:00
---
[[Process|Processes]] executing concurrently in the [[Operating Systems|OS]] may be either independent processes or cooperating processes. A process is **independent** if it does not share data with any other processes executing in the system. A process is **cooperating** if it can affect or be affected by the other processes executing in the system.

There are several reasons for providing an environment that allows process cooperation:
- **Information sharing:** Must provide an environment to allow concurrent access to information 
- **Computation speedup:** If we want a particular task to run faster, we must break it into subtasks, each of which will be executing in parallel with the others.
- **Modularity**: We may want to construct the system in a modular structure
- **Convenience**

Cooperating processes require an **interprocess communication** (IPC) mechanism that allows the exchange of data. There are two models of interprocess communication:
- **Shared memory**: A region of memory is shared by the cooperating processes
- **Message passing:** Communication takes place by means of messages exchange between cooperating processes. 
![[Pasted image 20230805222913.png|400]]

## IPC in Shared-Memory Systems
Interprocess communication using shared memory requires communicating processes to establish a region of shared memory. To illustrate the concept of cooperating processes, consider the producer-consumer problem. 

A producer process produces information that is consumed by a consumer process. For example, a compiler may produce assembly code that is consumed by an assembler. Or think of a server as a producer and a client as a consumer, a web-server will produce web content such as [[HTML]] files and images, which are consumed by the client web browser requesting the resource. The producer and consumer must be synchronised using buffers such that the consumer does not try to consume an item that has not yet been produced.
- **Unbounded buffer:** Places no practical limit on the size of the buffer. So the consumer may have to wait for new items, while the producer can always produce items.
- **Bounded buffer:** Assumes a fixed buffer size. So the consumer must wait if the buffer is empty, and the producer must wait if the buffer is full.

An example of how the bounded buffer will communicate using shared memory can be seen below. Here the two variables reside in a region of memory shared by the producer and consumer processes:
```c
#define BUFFER_SIZE 10 

typedef struct { 
	... 
} item; 

item buffer[BUFFER_SIZE]; 
int in = 0; // Points to next free position in the buffer
int out = 0; // Points to the first full position in the buffer
```
Here the variable `in` points to the next free position in the buffer and `out` points to the first full position in the buffer. The buffer is empty when `in == out` and the buffer is full when `((int + 1) % BUFFER_SIZE) == out`. 

The code below demonstrates how the producer and consumer can share memory, and how the producer will wait/check till the consumer has consumed and respectfully the consumer will wait/check till the producer has produced. This scheme allows at most `BUFFER_SIZE - 1` items in the buffer at the same time.

| Producer                             | Consumer |
| :------------------------------------: | :--------: |
| ![[C Code Snippets#^ProducerProcess2]] | ![[C Code Snippets#^ConsumerProcess2]]         |

One issue this illustration does not address concerns the situation in which both the producer process and the consumer process attempt to access the shared buffer concurrently.
## IPC in Message-Passing Systems
Another model for interprocess communication is message-passing. Message-passing provides a mechanism to allow processes to communicate and synchronise their actions without sharing the same address space (variables/memory). It is particularly useful in a distributed environment, where the communication processes may reside on different computers connected by a network.

A message-passing facility provides two operations:
- `send(message)` - messages can be either fixed or variable in size
- `receive(message)`

If processes $P$ and $Q$ want to communicate, they must:
- Establish a communication link between them
- Exchange messages via send/receive

The implementation of a communication link is not done physically (via shared shared or hardware bus) but rather logically implemented, using either of these methods:
- Direct or indirect communication
- Synchronous or asynchronous communication
- Automatic or explicit buffering

# Buffering
Whether communication is direct or indirect, messages exchange by communicating processes reside in a temporary queue. Basically, such queues can be implemented in three ways:
- Zero capacity: The queue has a maximum length of zero; this, the link cannot have any messages waiting in it. In this case, the sender must block until the recipient receives the message
- Bounded capacity: The queue has finite length $n$; thus, at most $n$ messages can reside in it. If the queue is not full when a new message is sent, the message is placed in the queue (either the message is copied or a pointer to the message is kept), and the sender can continue execution without waiting.
- Unbounded capacity: The queue's length is potentially infinite; thus, any number of messages can wait in it. The sender never blocks. 
The zero-capacity case is sometimes referred to as a message system with no buffering. The other cases are referred to as systems with automatic buffering.