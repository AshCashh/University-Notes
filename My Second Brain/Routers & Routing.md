---
alias: Router, Routers, Routing
---
#cs #networks 
Routers operate at the [[Open System Interconnection#Network Layer|Network Layer]] and are responsible for connecting separate logical [[Networks]] via data packets to form an internetwork, known as routing.
![[Pasted image 20230819093102.png|centre|400]]
Routing is one of the fundamental features of the [[Internet, Intranet, Extranet|Internet]] because it enables packets to pass from one device to another and reach its final destination. The routing process involves selecting the best route to reach such destination.
# Router Interfaces
Routers must have two or more interfaces (ports) in order to forward packets to other networks. Each interface on a router has full Networking functionality, including an IP  and MAC address. In fact, you can look at a interface as just a [[Network Interface Card|NIC]] with the [[Internet Protocol|IP]] bounded to it.

The following steps summarise how router uses its interface to forward packets from one network to another:
1. A router receives a frame on an interface
2. The router checks the frame's destination MAC address
3. If the destination MAC address matches the interface's address, the router reads the frame; otherwise, the frame is discarded
4. The frame header and trailer are stripped to create a packet
5. The destination IP address is checked
6. If the IP address's network ID is different from the interface network ID, the packet should be routed
7. The router consults the routing table to determine which of its interfaces the packet should be forwarded
8. The packet is encapsulated in a new frame header and trailer
9. The packet is forwarded to the destination computer or the next router in the path
![[Pasted image 20230819103620.png]]

# Routing Tables
Routing tables are composed of network address and interface fairs that tell the router which interface a packet should be forwarded to.

The routing table in most routers contain the following information for each table entry:
- **Destination network** (Dest. IP): The network address of a network to which the router can forward packets. Usually expressed in [[Classless Inter-Domain Routing|CIDR]] notation.
- **Next hop** (or gateway): Indicates an interface name or the address of the next router in the path to its destination. The total number of routers a packet must travel through is called the hop count
- **Metric** (or cost, distance): Numeric value that tells the router how "far away" the destination network is. 
- **Timestamp**: Tells the router how long it had been since the routing protocol updated the dynamic route. Not all routing protocols require a timestamp.

## Types of table entries:
Directly connected network:
- A directly connected network is a network that is directly attached to one of the router interfaces
- The network address/subnet mask of the interface, along with the interface type and number, are entered into the routing table as a directly connected network
Remote network:
- A remote network is a network that is not directly connected to the router. Namely, a remote network is a network that can only be reached by sending the packet to another router.
Default routes (quad-zero route):
- All packets for destinations are not established in the routing
- Expressed as `0.0.0.0/0`

# Routing Protocols
A routing protocol (static and dynamic routing) is a set of rules that routers use to exchange information so that all routers have accurate information about an internetwork to populate their routing routing tables.
