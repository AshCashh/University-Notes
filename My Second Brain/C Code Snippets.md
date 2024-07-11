---
tags: [cs]
Created: 2023-08-21T00:44:43+10:00
Modified: 2024-07-03T19:35:33+10:00
---


```c
while (true){
	wait(rw_mutex);
	...
	// Writing is performed
	...
	signal(rw_mutex);
}

```
^WriterProcess

```c
while (true) 
{ 
	wait(mutex); 
	read count++; 
	if (read count == 1){
		wait(rw_mutex);
	}
	signal(mutex); 
	... 
	/* reading is performed */ 
	... 
	wait(mutex); 
	read count--; 
	if (read count == 0) {
		signal(rw_mutex);
	} 
	signal(mutex); 
}
```
^ReaderProcess

```c
while(true){
	...
	// Produce an item in next_produced
	...
	wait(empty);
	wait(mutex);
	...
	// Add next_produced to the buffer.       
	...
	signal(mutex);
	signal(full);
}
```
^ProducerProcess3

```c
while(true){
	wait(full);
	wait(mutex);
	...
	// Remove an item from buffer to next_consumed
	...
	signal(mutex);
	signal(empty);
	...
	// Consume the item in next_consumed
	...
}
```
^ConsumerProcess3


```c
item next_produced;

while (true){
	// Produce an item in next_produced

	while (((in + 1) % BUFFER_SIZE) == out)
	{
		// Buffer is full. Do nothing
	} 
	buffer[in] = next_produced; // Next item stored
	in = (in + 1) % BUFFER_SIZE;
}
```
^ProducerProcess2

```c
item next_consumed;

while (true){
	while (in == out){
		// Buffer is Empty. Do nothing
	}
	next_consumed = buffer[out]; 
	out = (out + 1) % BUFFER_SIZE;
	// Consume the item in next_consumed
}
```
^ConsumerProcess2


```c
wait(S){
	while (S <= 0){
	} // Busy wait
	S--;
}
```
^wait




```c
signal(S){       
	S++;
}
```
^signal


```c
wait(semaphore *S){
	S->value--;
	if (S->value < 0){
		// Add this process to S->list
		block();
	}
}
```
^WaitModified

```c
signal(semaphore *S){
	S->value++;
	if (S->value <= 0){
		// Remove a process P from S->list
		wakeup(P);
	}
}
```
^SignalModified

```c
while (true){
	flag[1] = true;
	turn = 0;
	while (flag[0] && turn == 0);
		// critical section
	flag[1] = false;
		// remainder section
} 
```
^Process2

```c
// Producer process
while (true) { 
	/* produce an item in next produced */ 
	while (counter == BUFFER SIZE) {
	} /* do nothing */ 
		
	buffer[in] = next_produced; 
	in = (in + 1) % BUFFER SIZE; 
	counter++; 
}
```
^ProducerProcess

```c
// Consumer process
while (true){
	while (counter == 0){
	} /* do nothing */

	next_consumed = buffer[out]; 
	out = (out + 1) % BUFFER SIZE; 
	counter--;
	// consume the item in next_consumed
}
```
^ConsumerProcess

```c
acquire(){
	while (!available){
		// busy wait
	}
	available = false;
}
```
^acquire

```c
release(){
	available = true;
}
```
^release


```c
while (true){
	flag[0] = true;
	turn = 1;
	while (flag[1] && turn == 1);
		// critical section
	flag[0] = false;
		// remainder section
} 
```
^Process1

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h> 
#include <sys.sockets.h> 
#include <netinet/in.h>
#include <unistd.h>

int main()
{
	int fd = socket(AF_INET, SOCK_STREAM, 0); // file descripter

	// Setting socket options - saying its okay to reuse addr and port
	int opt_enable = 1;
	setsockopt(fd, SOL_SOCKET, SO_REUSEADDR, &opt_enable, sizeof(opt_enable));
	setsockopt(fd, SOL_SOCKET, SO_REUSEPORT, &opt_enable, sizeof(opt_enable));

	struct sockaddr_in addr;
	memset(&addr, 0, sizeof(addr));
	addr.sin_addr.s_addr = htonl(INADDR_ANY);
	addr.sin_family = AF_INET;
	addr.sin_port = htons(12345);

	bind(fd, (struct socketaddr *)&addr, sizeof(addr));

	listen(fd, 10); // Listen for input

	struct sockaddr clientaddr;
	socklen_t clientaddr_len;

	int clientfd = accept(fd, &clientaddr, &clientaddr_len);

	// Do stuff with socket
	char buf[1024];
	int bytes_received = recv(clientfd, buf, 1023, 0); // Receive data
	buf[bytres_received] = '\0';
	printf("Received from client: %s", buf);

	shutdown(clientfd, SHUT_RDWR); // Shut down

	// Close descripters
	close(clientfd); 
	close(fd);
}
```

^ServerSocket

```c

sdasd

#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <sys.sockets.h>
#include <netinet/in.h>
#include <unistd.h>
#include <arpa/inet.h>

int main()
{
	int fd = socket(AF_INET, SOCK_STREAM, 0); // file descripter

	struct sockaddr_in addr;
	memset(&addr, 0, sizeof(addr));
	inet_pton(AF_INET, "127.0.0.1", &addr.sin_addr) // Converts address and stores in addr.sin_addr
	addr.sin_family = AF_INET;
	addr.sin_port = htons(12345);

	connect(fs, (struct sockaddr *)&addr, sizeof(addr)); // Connect

	char *dataTosend = "Hello World\n";
	send(fd, dataTosend, strlen(dataTosend), 0); // Sending data

	shutdown(fd, SHUT_RDWR); // Shut down
	close(fd)
}
```

^ClientSocket


```c
g
```
^d