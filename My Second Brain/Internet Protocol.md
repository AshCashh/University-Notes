#cs
```
alias: IP
```
An Internet Protocol or IP address is assigned to every computer and network device using [[Internet Protocol Suite|TCP/IP]] for communication. IP addresses are used for two main reasons:
- To identify a network device at the Internetwork layer
- To identify the network on which a device resides

When a device receives an IP packet, it compares the destination IP address with its own:
- If it matches or is a broadcast, the packet is processed
- If it does not match then it is discarded

Every IP address contains two parts: 
- A network ID: Identifies the network broadcast domain
- A host ID: Identifies the host within the local network

# [[IPv4 Addressing|IPv4]] and IPv6
There are currently two versions of IP:
1. Internet Protocol version 4 (IPv4):
	- Most common IP version - Invented in 1977
	- 4.3 Billion unique IP addresses
2. Internet Protocol version 6 (IPv6):
	- Invented in late 1990s 

# IP Header Fields
![[Pasted image 20230803161837.png]]
- **Version Field**: Indicates whether IPv4 or IPv6
- **Header Length Field**: Denotes the length of the IP header only
- **Differentiated Service (DiffServ) Field**: Specifies a packets priority and informs routers the level of priority they should apply when processing the incoming packet
- **Total Length Field:** Defines the total length of the IP packet, including header and data

- **Identification Field (16 bits):** 
	- Each packet is given a unique ID value when sent
	- If packet is fragmented, same ID number is placed in each fragment
- **Flag Field (3 bits):** 
	- Specifies if fragmentation is allowed or not
	- Indicates if a packet is fragmented, if so whether it is the last or not.
		- First bit unused
		- D is Do not fragment bit
		- M is more fragment bit
- **Fragmentation Offset (13 bits)**
	- Shows where to place packets's data when fragments are reassembled into a single packet
	- The offset of the data in the original datagram measured in units of 8 bytes.
	- The first fragment has an offset of zero
	- It only records the 1st byte number of that fragmented packet

- **Time to Live (TTL) Field:** Denotes the remaining lifetime of the packet
- **Protocol Field:** Indicates the type of Transport layer protocol that received the packet (TCP or UDP)
- **Header Checksum Field:** Allow the receiver to calculate if the IP header has been corrupted during transmission

- **Source Address Field**: Indicates the IP address of the source node
- **Destination Address Field:** Indicates the IP address of the destination node
## IP Fragmentation
Fragmentation is necessary for data transmission, as every network has a unique limit, i.e. the maximum transmission unit (MTU), for the size of datagrams that it can process. If a datagram is being sent that is larger than the receiving server's MTU, it has to be fragmented in order to be transmitted completely. 

#### Fragmentation Offset Calculation Example
![[Pasted image 20230803165433.png]]



### Issues with IPv4 Fragmentation
Fragmentation causes more overhead (time and resources) for the receiver when reassembling the fragments because the receiver must allocate memory for the arriving fragments and combine them back into one datagram after all the fragments are received. If one fragment of an IPv4 datagram is dropped, then the entire original IPv4 datagram must be resent. 

## Routes Packets through an Internetwork
The Network layer determines the best way to get a packet from network to network until it reaches its destination. Most large internetworks (the internet) have multiple paths for getting from one network to another. Routers work at the Network layer and it is their job to select the best path to the destination. Routers use the network ID portion of IP addresses along with their routing tables to determine the best path.

## Resolves MAC Addresses from IP Addresses
Every frame contains both physical (MAC) and logical (IP) source and destination addresses. When a packet is ready to be sent to the Network access layer, the destination device's MAC address must be retrieved before the frame header can be constructed.
TCP/IP uses [[Address Resolution Protocol]] (ARP) to find MAC addresses.

## Delivers Packets Efficiently
Network layer protocols primarily focus on efficient delivery of packets. Features such as [[Flow Control]], delivery confirmation or message assembly are not included in network protocols; they require considerable overhead to ensure reliable delivery at the cost of efficiency. 

Network layer protocols rely on the protocols in the Transport and Application layers to provide reliability features, this is considered a **connectionless protocol**. Where upper-layer protocols ensure the packets safe journey.