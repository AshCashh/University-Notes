---
alias: Supernet
---
#cs #networks
Supernetting also known as network summarisation, is the direct opposite of [[Subnetting]], in which multiple [[Networks]] are combined into a single large network known as supernets. Supernetting reallocates bits from the network portion of an [[Internet Protocol|IP]] address to the host portion, effectively making two or more smaller subnets into a larger supernet.

It is used for route aggregation to reduce the size of routing tables. Here's how it works:
1. Suppose you have four class C network addresses - `192.168.0.0/24`, `192.168.1.0/24`, `192.168.2.0/24`, and `192.168.3.0/24` which has a total 900 hosts on the proposed network. You can combine the four networks into one be reallocating 2 bits ($2^2 = 4$) from the network portion of the address and add them to the host portion. Resulting in network address of `192.168.0.0/22` with the super subnet mask `255.255.252.0`
2. Instead of supporting only 8 bits for the host address portion, the supernet now supports 10 bits (8 + 2) for host addresses. This provides $2^{10}-2$ host addresses on this supernet, which satisfies your required 900 total hosts needed.
3. You can verify the network ID using the super mask and the AND operation. If done correctly, it should result in the first subnet (`192.168.0.0`). I.e. `192.168.3.16` & with `255.255.252.0` results in `192.168.0.0` (first subnet)
![[Pasted image 20230811115609.png|centre|400]]
## Benefits of Supernetting
The main objective of supernetting is to simplify or summarise network routing decisions and minimise processing overhead when matching routes, as well as reduce storage space of route information on routing tables. By supernetting you improve the networks stability, reduce processor workloads, memory requirements and bandwidth demand.

# Subnetting vs Supernetting

| Subnetting                                                    | Supernetting                                                               |
| ------------------------------------------------------------- | -------------------------------------------------------------------------- |
| Divides a network into a group of smaller networks            | Combining a group of continuous network addresses to form a single network |
| Reduces and better manages broadcast domains                  | Reduces the number of entries in a routing table                           |
| Host bits are borrowed to be used as a subnet ID              | Network bits are borrowed to be used as the host ID                        |
| Manipulates the network mask to divide a network into subnets | Manipulates the network mask to form a supernetwork                            |



