---
alias: CIDR
---
#cs #networks 
Classless Interdomain Routing (CIDR) is a method of assigning [[Internet Protocol|IP]] addresses that improves the efficiency of address distribution and replaces the previous [[IPv4 Addressing#IP Address Classes|Class]] based system on [[Networks]]. 

The initial goal of CIDR was to slow the increase of routing tables on [[Routers & Routing|Routers]] across the internet and decrease the rapid exhaustion of [[IPv4 Addressing|IPv4 Addresses]]. As a result, the number of available internet addresses has greatly increased.

# CIDR Notation
Writing IP addresses with their subnet masks can be tedious and takes up a lot of space. What's important is how many bits of the IP address constitute the network ID. To that end, you can specify an IP address and its subnet mask with CIDR notation. 

For example, `172.31.210.10` with a `255.255.255.0` subnet mask is expressed as `172.31.210.10/24` in CIDR or slash notation. The network ID is 24 bits, leaving 8 bits for the host ID.