---
aliases:
  - ARP
tags:
  - networks
Created: 2023-09-08T00:00:00+10:00
Modified: 2024-07-03T19:35:33+10:00
---
Address Resolution Protocol (ARP) is used to resolve a logical ([[Internet Protocol|IP]]) address to a physical (MAC) address for local [[LAN, WAN, MAN|LAN]] communication. It operates at both the Network and Data Link layer of the [[Open System Interconnection|OSI]]. 

When a packet is ready to be sent to the Network access layer, the destination device's MAC address must be retrieved before the frame header can be constructed. The source device needs to obtain the MAC address of the destination device to deliver data.

An ARP is a request/reply pair of transmissions on the local network. The originator transmit a broadcast, requesting the hardware address of the target host. The target host then replies unicast back to the originator with the hardware address of the target host.
# General Operation
When an originator on an IP-based network has an IP datagram to send to a target host, it will first check if the target host's MAC address is in the ARP cache or not, then it will start the required address resolution process. 

If the target host is on the same network:
- Then it will send a broadcast ARP request to the network and wait for the ARP reply
Else if the target host is not located on the same network:
- It will send the datagram to one of the default gateway (router) on the network for forwarding data.
# ARP Cache
To avoid sending an ARP request every time an IP packet is sent, PCs and other devices store learned IP address-MAC address pairs in an ARP cache, a temporary location in RAM.

ARP cache entries are not kept indefinitely, most devices keep an ARP entry only for a few minutes after it is last used to avoid storing outdated information, which could result from a changed NIC or IP address.

An ARP request is sent as a broadcast message, so that every host on that network records the mapping of requester's IP and AC addresses to its ARP cache table for future reference.
# ARP Request & Reply
ARP is a two-step process: a request and a reply. Within a network, when originator -host A, begins a conversation with a target - host B:
- A is aware of B's IP address but does not have the B's MAC address. A is unable to send a unicast from to B
- A sends an ARP broadcast frame to request B's MAC address. Since it is a broadcast, all hosts on the same network receives the ARP request
- All hosts scan the contents of the ARP request to determine if they are the intended target. The hosts which are not the intended target discard the broadcast frame.
Since B is the target of the ARP request:
- It will send an ARP reply back to A. Since B knows who sent the initial ARP request, it can send the ARP response unicast, directly back to A
![[Pasted image 20230826155909.png]]

# Examples
## Direct Delivery A -> B
![[Pasted image 20230826160209.png|centre|300]]
A sends out a broadcast ARP request message:
- B, C and D receive this broadcast message but discard it as it isn't intended for them
Only B will respond with a unique ARP reply message to A

## Indirect Delivery A -> C
![[Pasted image 20230826160336.png|centre|300]]
A sends out a broadcast ARP request message to request the routers MAC address:
- The router responds with an ARP reply message via unicast
- The router upholds the received data and then processes the reply:
	- The router sends out a broadcast ARP request to request for C's MAC address
	- C responds with an ARP reply message via unicast
	- The router re-packages the data (Layer 3 and 2) then forwards the frame to C
