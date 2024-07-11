---
alias: ICMP
tags: [cs, networks]
Created: 2023-08-26T18:07:33+10:00
Modified: 2024-07-03T19:35:33+10:00
---
Internet Control Message Protocol (ICMP) is used to send error, status and control messages between systems or devices. It's an encapsulated [[Internet Protocol|IP]] protocol, meaning it's wrapped in an IP header. In essence, ICMP is just a specialised IP packet with its own header and falls within the Network layer in [[Open System Interconnection|OSI]].

ICMP is used by routers and hosts and assists with the diagnosis of some network problems, performing error reporting and query/reply for the IP. It however only returns error messages back to the originator (the sender). 
Report errors include:
- Invalid IP address or port address
- TTL = 0 of the packet (time to live)
# Types of ICMP
ICMP has many message types, but the two most people know are ICMP Echo (sent by the `ping` program) and ICMP Echo Reply (the reply, sent by the target of the ping).
![[Pasted image 20230826185836.png|centre|300]]
`ping` uses ICMP Echo packets to request a response from another computer to verify whether its available for communication. The response, if received is an ICMP Echo Reply packet indicating not only that the remote host is reachable but also how long the message's round trip from sender to receiver took.

# Format of ICMP Messages
![[Pasted image 20230905082609.png|centre|500]]
Here we can see the ICMP message format and also the list of three commonly used ICMP types 0, 3 and 8. Each ICMP message starts with an 8-bit Type field, an 8-bit Code field, followed by a computed 16-bit Checksum field.
![[Pasted image 20230905082830.png|centre|400]]
Here is a list of three common types of ICMP messages with associated codes. The code field provides further information to the Type field about the nature of the problem.
# Destination Unreachable
When a router cannot forward a datagram, it sends a destination unreachable message to the originator and then discards the datagram.
# Time Exceeded
Incorrect configurations can lead to packets traveling to endless loops (routing cycle). The ICMP Time Exceeded message is issued:
- When a packet is sent, its TTL is decremented by 1 at each hop. If the TTL reaches 0, the packet is dropped. The router that dropped the IP packet for which the TTL reached 0 sends a time-exceeded message to the originator
- If destination does not receive all fragments in a set time, it drops any received fragments and sends a time-exceeded message back to the originator
# Echo Request/Reply
A host or router that receives an echo-request message creates an echo-reply message and returns it to the originator. Echo-request and echo-reply messages can be used to help diagnose some network problems, e.g. communication status between two devices. Testing destination reachability and providing status is achieved by invoking a ping command. 
## Tracert
The `tracert` program uses ICMP Echo packets to determine the route a packet takes through an internetwork. It sends an ICMP Echo packet with the TTL value in the IP header set to 1. When the packet reaches the first router on its way to the destination, the router decrements the TTL value to 0, discards the packet and sends a TTL-Expired ICMP packet to the sending machine to notify it that the packet expired. `tracert` receives the TTL-expired message containing the routers IP address and then has the address of the first router in the path to the destination. Next, `tracert` sends an ICMP Echo packet with a TTL of 2. When the packet gets to the second router, it again expires and the second router sends a TTL-expired message. In this way, `tracert` discovers the IP address of every router between the source and destination computers.
![[Pasted image 20230826191810.png|500]]

