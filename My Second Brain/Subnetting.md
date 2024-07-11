---
aliases:
  - Subnet
tags:
  - cs
  - networks
Created: 2023-08-10T20:42:43+10:00
Modified: 2024-07-03T19:35:33+10:00
---
Subnetting is splitting up a [[Networks|Network]] address range into a group of smaller networks. The end result is multiple smaller sub-networks. For example, you could use `172.31.0.0/24`,  `172.31.1.0/24` and so forth up to `172.31.255.0/24`

There are two approaches to subnetting an [[Internet Protocol|IP]] address. Fixed length subnet mask (FLSM) and variable length subnet mask ([[Subnetting#VLSM|VLSM]]). In FLSM subnetting, all subnets are of equal size with an equal number of hosts identifiers/addresses. This method tends to be the most wasteful because it uses more IP addresses than necessary.

## Purpose of Subnetting 
One reason to subnet is to conserve IP addresses, as it will enable the reduction and management of broadcast domains, reduce congestion, etc. Subnetting also divides a network into logical subnets (i.e. department/divisions). It supports different network technologies (Ethernet/WiFi). Subnets will support WANs by allowing geographically separated LANS to use a single network ID.

## Calculating a Subnet Mask
1. First decide how many subnets you need (how many times do you want to split the network in sections)
2. Decide how many bits you need to meet or exceed the number of required subnets. Use $2^n$ where $n$ is the number of bits needed to reallocate the host ID to the network ID.
3. Reallocate bits from the host ID, starting from the MSB
4. Ensure there are enough host bits available to assign to each PCs on each subnet. The number of host addresses available use: $2^n-2$ with $n$ representing the number of host bits in the subnet mask.

Example: 
1. 60 subnets for Class B address: `172.20.0.0/16` 
2. Nearest power of 2 is 64: $2^6$. 
3. Therefore, 6 bits need relocating from the host portion of the original subnet mask (`255.255.0.0`) and make them subnet bits. Becomes `255.255.252.0` or in [[Classless Inter-Domain Routing|CIDR]] (slash) notation gives you `172.20.0.0/22
4. Host addresses for each subnet: Subtract number of network ID bits from total bits: $32-22$ which results in the bits left for the host ID (10). Number of host addresses: $2^{10}-2=1022$ addresses per subnet.

Example 2:
ISP has allocated a block of addresses `193.64.33.0/24`. We need 8 subnets.
So subnet mask becomes: `255.255.255.224`, As we've allocated 3 of the MSB.
![[Pasted image 20230810222917.png|centre|400]]
The 8 subnet usable address ranges would consist of intervals of 30 ($2^5-2=30$) starting at `193.64.33.1` to `193.64.33.30` for the first subnet then `193.64.33.31` becomes the broadcast address and `193.64.33.32` is the networking address so the second subnet starts at `193.64.33.33` to `193.64.33.62`, and so on:
![[Pasted image 20230810224235.png|centre|300]]
First range:
![[Pasted image 20230810224418.png|centre|400]]
Second range: 
![[Pasted image 20230810224431.png|centre|400]]

# VLSM
Variable Length Subnet Mask is a subnet design that allows all subnet masks to have variable sizes. IP address spaces can be divided into subnets of subnets with different sizes, and allocate it according to the individual needed on a network.

Suppose a C class address `212.5.5.0/24` that requires 3 subnets with 60 hosts and 2 with 30 hosts. The solution is to subnet a subnet, borrow 2 more bits from the host portion:
- Gives 4 subnets (2 bits for subnet) with 60 hosts each (6 bits from host portion)
Then further subnet one of the 4 subnets by borrowing an additional 1 bit from the host portion.

3 subnets with 60 each hosts:
![[Pasted image 20230811110619.png|centre|500]]
2 subnets with 30 hosts each:
![[Pasted image 20230811110550.png|centre|500]]