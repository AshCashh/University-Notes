---
alias: UDP
---
#cs #networks 
User Datagram Protocol or UDP is a connectionless [[Open System Interconnection#Transport Layer|Transport Layer]] protocol designed for efficient communication of generally small amounts of data.

The features on UDP consist of:
- No connection handling (no handshakes required): Each datagram is an independent message that the sender transmits without UDP providing any way to establish, manage or close a connection
- No delivery guarantees: 
	- Data grams are not sequenced and are not acknowledged 
	- Datagrams are sent without any promise of delivery
	- Application layer must provide tracking and retransmission mechanisms
- No error checking (checksum): No guarantee that packets are received at all

# UDP Format
![[Pasted image 20230826151438.png]]
Each UDP message is called a user datagram. The header has a fixed size of 8 bytes:
- Source / Destination: 16 bit fields
- Checksum is optional for IPv4

# Applications 
UDP is used while error checking and correction is performed by the application layer, such as:
- Domain Name System (DNS)
- [[Dynamic Host Configuration Protocol]] (DHCP)
- Trivial File Transfer protocol (TFTP)
- Real Time Streaming Protocol 
- Routing Information Protocol 