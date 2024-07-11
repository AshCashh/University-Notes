---
tags: [os]
Created: 2023-09-04T09:17:02+10:00
Modified: 2024-07-03T19:35:33+10:00
---
# Server Side
Note: error checking not implemented
```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h> // Not entirely necessary
#include <sys.sockets.h> 
#include <netinet/in.h>
#include <unistd.h>

int main()
{
	int fd = socket(AF_INET, SOCK_STREAM, 0); // listeing socket file descripter
	if (fd == -1){
		perror("fd()");
		exit(1);
	}
	// Setting socket options - saying its okay to reuse addr and port
	int opt_enable = 1;
	setsockopt(fd, SOL_SOCKET, SO_REUSEADDR, &opt_enable, sizeof(opt_enable));
	setsockopt(fd, SOL_SOCKET, SO_REUSEPORT, &opt_enable, sizeof(opt_enable));

	struct sockaddr_in addr;
	memset(&addr, 0, sizeof(addr)); // Wipe address to 0s
	addr.sin_addr.s_addr = htonl(INADDR_ANY); // Seting as server, others connect to us
	addr.sin_family = AF_INET; // Adress family
	addr.sin_port = htons(12345); // Set port number

	bind(fd, (struct socketaddr *)&addr, sizeof(addr));

	if (listen(fd, 10) == -1){ // Listen for input - backlog of 10
		perror("setsocket()");
		exit(1);
	}
	
	struct sockaddr_in clientaddr;
	socklen_t clientaddr_len = sizeof(clientaddr); // Size of addr

	int clientfd = accept(fd, &clientaddr, &clientaddr_len); // accept
	if (clientfd == -1){
		perror("accept()");
		exit(1);
	}
	
	// Do stuff with socket
	char buf[1024];
	int bytes_received = recv(clientfd, buf, 1023, 0); // Receive data
	if (bytes_received == -1){
		perror("receive()");
		exit(1);
	}
	
	buf[bytres_received] = '\0';
	printf("Received from client: %s", buf);

	if(shutdown(clientfd, SHUT_RDWR) == -1){ // Shut down for read/write
		perror("shutdown()");
		exit(1);
	}
	// Close descripters
	close(clientfd); 
	close(fd);
}
```
If want to continuously read data, implement an infinite loop from `int clientfd = accept(...)` to `close(clientfd);

# Client Side
```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h> // Not entirely necessary
#include <sys.sockets.h> 
#include <netinet/in.h>
#include <unistd.h>
#include <arpa/inet.h>

int main()
{
	int fd = socket(AF_INET, SOCK_STREAM, 0); // file descripter
	if (fd == -1){
		perror("fd()");
		exit(1);
	}
	struct sockaddr_in addr;
	memset(&addr, 0, sizeof(addr));
	const char *ipaddress = "127.0.0.1";
	inet_pton(AF_INET, ipaddress, &addr.sin_addr); // Converts address and stores in addr.sin_addr
	addr.sin_family = AF_INET;
	addr.sin_port = htons(12345);

	if (connect(fs, (struct sockaddr *)&addr, sizeof(addr) == -1){ 
		perror("connect()");
		exit(1);
	} 

	char *dataTosend = "Hello World\n";
	if (send(fd, dataTosend, strlen(dataTosend), 0)){; // Sending data
		perror("send()");
		exit(1);
	}
	shutdown(fd, SHUT_RDWR); // Shut down
	close(fd)
}
```
## Endians Commands
```c
// Host byte order short - Host to network short
printf("htons(%d) = %d\n", <port>, htons(<port>)); 
// Host byte order long
printf("htonl(%d) = %d\n", <port>, htonl(<port>)); 
// Network byte order short 
printf("ntohs(%d) = %d\n", <port>, ntohs(<port>));
// Network byte order long
printf("ntohl(%d) = %d\n", <port>, ntohl(<port>));
```
They convert between host byte order (host machine) to the the network byte order, or vice verse Which can be either a short (`htons()`) or a long (`htonl()`).
Where byte order is how we store the data. i.e. Endianness. 
### Example
Passing a port `12345`. 
```c
htons(12345) = 14640
htonl(12345) = 959447040
htohs(12345) = 14640
ntohl(12345) = 959447040
```
In hex:  `12345 = 0x3039`. 
Little endian: `12345 = 39 30 00 00 = 14640`  
Big endian:    `12345 = 00 00 30 39 = 959447040` 

Demonstrated using unsafe casting:
```c
int val = 12345; // 4 bytes
unsigned char *cval;
cval = &val;

// Inspect values of val (bytes)
printf("%d = %x %x %x %x\n",val, cval[0], cval[1], cval[2], cval[3]);
// Prints: 12345 = 39 30 0 0
```
## Sending/Receiving Multiple Packets
Client side:
```c
// Message sending function
void sendMessage(int fd, const char *message){
	int len = strlen(msg);
	uint32_t netLen = htonl(len); // Guarentees int is always 32 bits
	send(fd, &netLen, sizeof(netLen), 0); // Send data
	if (send(fs, msg, len, 0) != len){
		fprintf(stderr, "Message was not right lenght");
		exit(1);
	}
}
char *dataToSend = "12345\n";
sendMessage(fd, dataToSend);
sleep(5); // Wait until sending next data
sendMessage(fd, dataToSend);
```
Server side:
```c
// Message receiving function
char * recvMessage(int fd){
	char *msg;
	uint32_t netLen;

	int recvLeng = recv(fd, &netLen, sizeof(netLen), 0);
	if (recv(fd, &netLen, sizeof(len), 0) != sizeof(netLen)){
		fprintf(stderr, "Recv invalid length (got %d)\n", recvLen);
		exit(1);
	}
	len = ntohl(netLen);
	msg = malloc(len + 1); // + 1 for null terminator
	if (recv(fd, msg, len, 0) != len){
		fprintf(stderr, "recv got invalid length message\n");
		exit(1);
	}
	msg[len] = '\0';

	return msg;
}
// Receiving messages
char *msg1 = recvMessage(clientfd);
printf("msg1: %s\n", msg1);
char *msg2 = recvMessage(clientfd);
printf("msg2: %s\n", msg2);

// Deallocate data
free(msg1);
free(msg2);
```
# Netcat
Used for testing network connectivity.
### Netcat client:
```c
nc localhost <port>
// Send bytes
```
Will send "Hello, World" to server
```c
echo "Hello, World" | nc localhost <port>
```
Send file data:
```c
nc localhost <port> < data.txt
```
### Netcat server:
```c
nc -l -p <port> // Bind and listen on 12345 port
```
Redirect data to file:
```c
nc -l -p <port> > out.txt
less out.txt // Read data
```