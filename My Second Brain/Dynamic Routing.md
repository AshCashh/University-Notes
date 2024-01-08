#cs #networks 
Dynamic routing is when the [[Routers & Routing|Routers]] themselves communicate with each other, exchanging routing information. The process involves three main stages:
1. Initialisation
2. Sharing
3. Updating
Before the router can process and calculate the received routing information, a network administrator must define which routes are to be advertised on a router. Convergence is achieved when a set of routers have the same topological information from each other.

**Dynamic routing is preferred when:**
- The network is of medium-large size or complex
- There is automatic updating of routing table entries facilitated by a routing protocol
## Advantages 
- Suitable in all topologies where multiple routers are required
- Automatically adapts topology to reroute traffic if possible
- Ability to sense and recover from network faults. If a router goes down, other routers can detect the fault and update the routing table accordingly
## Disadvantages
- Can be more complex to implement than static routing
- Requires additional resources such as CPU, memory and link bandwidth for routing updates
# Dynamic Routing Protocols
Dynamic routing protocols come in two categories: interior gateway protocol (IGP) and exterior gateway protocol (EGP). 
![[Pasted image 20230820125930.png]]

## Interior Gateway Routing Protocol
IGP is used for routing inside an autonomous system (AS), which is an internetwork managed by a single organisation, e.g. [[Dynamic Routing#Routing Information Protocol|RIP]], EIGRP, [[Dynamic Routing#Open Shortest Path First|OSPF]].

## Exterior Gateway Protocol
EGP are used for routing between autonomous systems, such as between an organisations network and an ISP or between two ISPs, e.g. Border Gateway Protocol (BGP).
# Dynamic Routing Algorithms
## Distance Vector Algorithm
Based on the Bellman Ford Algorithm, the distance vector algorithm is a dynamic routing algorithm where:
- On boot, a router initialises its routing table to contain an entry for each directly connected network
- Each router periodically shares its knowledge about the entire routing table to all its interfaces, e.g. "I can reach destination V at distance D via X"

Distance vector routers periodically broadcast/multicast their route information on directly connected links. Because of this it does tend to perform poorly in large networks.

## Link State Algorithm 
Based on the Dijkstra's Least-Cost algorithm, the algorithm finds all possible paths between two locations and in doing so, gets the least cost path. It does this by having each router generate information about only its direct connected links, hence building adjacencies with neighbouring routers. Most common implementation: Open Shortest Path First (OSPF).
![[Pasted image 20230820133413.png|300]]

Link state advertisements (LSAs) are exchanged throughout the network in order to update routing tables. LSAs are advertised only upon startup and when changes in topology are detected (not periodically).
## Routing Information Protocol 
Routing Information Protocol (RIP) is the most popular and best-known distance-vector routing protocol on the internet. It uses hop count as the metric to determine the best path to a destination network.

During an initialisation process, a router sends out a copy of its own routing table through all its interfaces, and updates every 30 seconds.

### Example
Suppose that Router A has learnt 4 routes to Networks BNE-SYN, SYN-MEL, MEL-ADL and ADL-PER (read as Brisbane to Sydney, etc):
![[Pasted image 20230820131902.png|centre|300]]
Now suppose Router D sends out the following routing information:
![[Pasted image 20230820132021.png|centre|300]]
Router A will look at each entry in Router's D table and make the following decisions:
![[Pasted image 20230820132411.png|centre|300]]
![[Pasted image 20230820132529.png|centre|400]]
First Router D's table will increment the metric by 1 as its 1 hop to reach router D.
Router A will then look at each destination network and assess if it needs to update its chart or not. If the path is shorter (i.e. BNE-SYN is 5 from D, while from A, its 8), router A will update its table accordingly. 
## Open Shortest Path First 
A form of link state routing known for its adaptability and distribution but far more complicated than RIP and performed much better.

Link state process:
- Routers 1st learn of directly connected networks'
- Routers then say "Hello" to neighbours -> build link state packets.
- They then flood LSPs to all neighbours and use LSP database to build a network topology map that calculates the best path to each destination