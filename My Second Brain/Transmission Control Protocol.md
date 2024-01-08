---
alias: TCP
---
#cs #networks 
If an application requires reliable data transfer, it uses TCP as the [[Open System Interconnection#Transport Layer|Transport Layer]] protocol. TCP provides reliability with the following features that aren't available in [[User Datagram Protocol|UDP]]:
- Establishing a connection
- Data Transfer
- Ensuring [[Flow Control]] with acknowledgements
Each feature relies on TCP being a connection-oriented protocol. TCP establishes a three-way handshake connection with the destination, data is transferred and after data transmission, the connection is terminated by a four-way handshake. TCP provides error control using Retransmission Time Out (RTO)

# TCP Header
![[Pasted image 20230825214137.png]]
- Source port address: 16 bit field that identifies the sending port
- Destination port address: 16 bit field that identifies the receiving port
- Sequence number: 32 bit field that defines the 1st byte of datagram
- Acknowledgement number: 32 bit field that indicates explicitly that a specific set of data was received successfully
- Control 9 bit field: A set of 6 standard and 3 extended control flags: indicates the purpose and contents of the segment
	- ACK: Indicates the device sending the segment an acknowledgement that it was received
	- SYN: Indicates that the segment is being used to initialise a connection 
	- FIN: Indicates no more data from sender
- Window size: 16 bit field indicating the size of the TCP receiver buffer in bytes
- Checksum: 16 bit field for the integrity of the header and data
- Urgent pointer: 16 bit field thats used with the URGENT flag to point to the end of urgent data sent in a segment

# Establishing a Connection: The 3-way Handshake
Establishing a connection with TCP is similar to making a phone call. You dial the number and wait for your party to answer, usually with a greeting. The caller then states his or her name and says who he or she wants to talk to. If everything is agreeable, a conversation starts.

A TCP sessions begins with a 3-way handshake to initialise and synchronise the connection. This connection remains open for the duration of the interaction between the two ends. For example, a client A sends a TCP synchronisation SYN segment to the destination device B, usually a server. A destination port number is specified and a source port number is assigned dynamically. When the server receives the SYN segment, it responds by sending one of two segments: 
- An acknowledge-synchronisation (SYN-ACK) segment: Then, the client completes the three-way handshake by sending an ACK segment back to server (the client is ready to send/request data)
- A reset connection (RST) segment: Meaning, the server refused the request to open a session. If a SYN-ACK segment is returned
![[Pasted image 20230825223043.png]]

# Data Transfer 
When TCP receives data from the Application layer, the size of the data might be too large to send at once. TCP's job is to break the data into smaller segments before handling each segment to the Internetwork layer. 

Receipt of data must be acknowledged with an ACK that specifies the byte number that the receiver is expecting to receive from the sender. Each segment is labeled with a sequence number in order to track and identify the amount of data being transferred and any out of ordered packets.
![[Pasted image 20230825224830.png]]

# Connection Termination: 4-way Handshake
Four segments need to be exchanged to terminate a TCP connection:
- Since a TCP connection is full-duplex, data may flow independently in each direction
- Each direction must shut down independently TCP half-close
- Each half-close requires a FIN and ACK segment to be sent
![[Pasted image 20230825225600.png]]
