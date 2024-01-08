#cs #networks 
Static routing is when a network administrator, with knowledge of the network topology, manually builds and updates the routing table. This is an effective method for configuring and managing a routing table for small and predicable networks. However, it does not scale well for large or dynamically changing networks.

![[Pasted image 20230820104112.png]]
Below is an example routing table for a static route. The right hand table (yellow), is an improved version that aggregates `190.0.2.0/24` & `192.0.3.0/24` using [[Supernetting]],  and implements a default route.
![[Pasted image 20230820104949.png]]
The default route is set to [[Static Routing#ISP Router|ISPs Router]] interface thats facing towards R1 (which will handle internet traffic and any other possible traffic)

Static routing is preferred when:
- The network consists of only a few routes
- The ISP represents the only exit point to the internet
- A network is configured in a hub-and-spoke topology (central hub with single path branches)
- Access a single default route
## Advantages
- Easy to implement and maintain in small networks
- Very little overhead, no needs for a routing algorithm with no extra resources
## Disadvantages 
- Not easy to implement in large networks
- If a link fails, a static route cannot reroute traffic and will need to be fixed manually
# ISP Router
For the above example, the ISP routing table can be seen below as well as the aggregated version.
![[Pasted image 20230820105945.png]]
