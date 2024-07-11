---
tags: [networks]
Created: 2023-10-08T14:43:38+10:00
Modified: 2024-07-03T19:35:33+10:00
---
IPv6 is the next generation of the [[Internet Protocol]]. It is a 128-bit addressing scheme that is designed to replace [[IPv4 Addressing|IPv4]]. 

IPv6 is a major upgrade from IPv4 as it has:
- Abundant address space
- Auto-configuration
- Quality of Service
- Built-in security
- Mobile IP
- IPv6 address structure provides a hierarchy for future growth to facilitate core routing 
- Eliminates the need for NAT
- Broadcast is replaced with multicast
- Simplified header structure
- Removed header checksums

IPv6 uses slash notation with the decimal number after the slash representing the number of bits for the network portion of the address, for example: `2001:0DB8:2021:2022::/64`,`2001:0DB8:2021::/48`, `2001:0DB8::/32`.

IPv6 has some vulnerabilities however:
- Managing IPv6 addresses is more complex than IPv4
- IPv6 address scanning is difficult with how many addresses there are
- IPv6 introduce new security threats such as Transition, Extension Header Manipulation, Neighbour Discovery, DHCPv6 and more
- IPv6 and IPv4 do share common threats like Flooding, man-in-the-middle, Routing threats and more

# IPv6 Header
![[Pasted image 20231008144925.png]]
- Traffic Class: Classifies IPv6 packet priority 
- Flow Label: Used to identify packets that belong to the same flow
- Hop Limit: The maximum number of hops that a packet can make before it is discarded
- Payload Length: The length of the payload in bytes, including both the data and any extension headers.

# IPv4 vs IPv6
|                      |                                           IPv4                                            |                              IPv6                               |
| -------------------- |:-----------------------------------------------------------------------------------------:|:---------------------------------------------------------------:|
| Address Length:      |                                          32-bit                                           |                             128-bit                             |
| Address Notation:    |                      Decimal Values w/ 4 octets separated by periods                      | Hexadecimal values with 8 groups of 16 bits separated by colons |
| Address Space        |                                      $2^{32}$ (4.2B)                                      |                 $2^{128}$ ($3.4\times 10^{38}$)                 |
| Header Length        |                              Variable length of 20-60 bytes                               |                    Fixed Length of 40 bytes                     |
| No. of Header Fields |                                            13                                             |                                8                                |
| Common Fields        |                                       Version, TTL                                        |                       Version, Hop Limit                        |
| Distinction          | 1 field DSCP for QoS, 3 fields for fragmentation, Header checksum, variable header length | 2 fields for QoS, No header checksum, Fragmentation only done by sender, No total length                                                                |

# IPv6 Transition Mechanisms
- Dual Stack: A network that supports both IPv4 and IPv6. This however, does not necessarily fix the issue of IPv4 address depletion as it still requires IPv4 addresses to be used.
- Tunnelling: A method of encapsulating IPv6 packets within IPv6 packets or visa verse.
- Translation: A method of mapping IPv6 packets to IPv6 packets and visa versa. This however, negates most of the compelling reasons for using IPv6 such as hierarchical routing, expanded address space, and streamlined IP headers