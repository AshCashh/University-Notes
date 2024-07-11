---
tags:
  - networks
Created: 2023-08-11T00:00:00+10:00
Modified: 2024-07-03T19:35:33+10:00
---
Here we will work through some [[Networks|Network]] [[IPv4 Addressing|IPv4 Addresses]] and [[Subnetting|Subnet]] Masks to determine relevant networking information:

## Network Address
The network address is the address by which we refer to a network, it is not a valid address assigned to a host.

To identify the network address from a given IP address & subnet mask, simply perform a bitwise [[Logical Operators#Conjunction (AND)|AND]] operation on the two:

|                               |          |          |          |          |
| ----------------------------- | -------- | -------- | -------- | -------- |
| IP Address (in Binary):       | 11000001 | 00000010 | 00000001 | 00001001 |
| Subnet Mask (in Binary):      | 11111111 | 11111111 | 11111111 | 00000000 |
| Network Address (in Binary):  | 11000001 | 00000010 | 00000001 | 00000000 |
| Network Address (in Decimal): | 193      | 2        | 1        | 0        |

## Broadcast Address
The broadcast address is used to send datagrams to all the hosts on a network. It can be obtained by taking the host's IP address and set '1' to any bit positions which hold a '0' in the [[IPv4 Addressing#IP Address Classes|Host ID]].

|   |   |   |   |   |
|---|---|---|---|---|
|Network Address (in Binary):|11000001|00000010|00000001|00000000|
|Broadcast Address (in Binary):|11000001|00000010|00000001|11111111|
|Broadcast Address (in Decimal):|193|2|1|256|

## Usable Host Addresses
Each host in a network needs a unique IP address that is in the range of the network address and the broadcast address. Using the number of Host-ID bits, you can derive the total number of usable hosts for a network.
$$\text{Usable Hosts}=2^n-2$$
Hence for a Class C address which has 8 Host ID bits:
$$2^8-2=254\space \text{Addresses}$$
## Range of Usable Host Addresses
The first valid IP address is always the network address incremented by 1. To get the subsequent host addresses, you must increment by 1 until all the bits for the Host ID become all 1s. This becomes the broadcast address, the last one is the address before the broadcast.

|                        |            |          |          |          |
| ---------------------- |:----------:| -------- | -------- | -------- |
|                        | Network-ID |          |          | Host-ID  |
| IP Address             |  11000001  | 00000010 | 00000001 | 00001001 |
| Subnet Mask            |  11111111  | 11111111 | 11111111 | 00000000 |
| Network Address        |  11000001  | 00000010 | 00000001 |     00000000     |
| First Host IP address  |  11000001  | 00000010 | 00000001 |     00000001     |
| Second Host IP address |  11000001  | 00000010 | 00000001 |    00000010      |
| Third Host IP address  |  11000001  | 00000010 | 00000001 |    00000011      |
|                |      $\vdots$      |          |          |          |
| Last Host IP address   |  11000001  | 00000010 | 00000001 |     11111110     |
| Broadcast Address      |  11000001  | 00000010 | 00000001 |    11111111      |

