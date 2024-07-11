---
alias: DHCP
tags: [networks]
Created: 2023-09-02T13:51:32+10:00
Modified: 2024-07-03T19:35:33+10:00
---
Dynamic Host Configuration Protocol (DHCP) is used to automatically assign IP addresses as needed within a network. 
- When a computer is turned it, it will request an address from a DHCP server that is configured as a DHCP server with a block of available IP addresses
- The DHCP server assigns an address to the computer for a specific amount of time (called a lease)
DHCP servers listen on [[User Datagram Protocol|UDP]] port `67` for IP address releases, while DHCP clients use port `68` for IP address requests.
# DHCP Server
A DHCP server is composed of the following:
- **IP Address Scope:** A range of IP addresses the server leases to clients that request an IP address. In Windows, a scope is specified with starting and ending IP addresses, a subnet mask and the lease time. After the scope is created, an administrator can further configure it using the following:
	- **Scope Options:** IP settings - such as the default gateway, DNS servers, domain name or the router.
	- **Reservations:** An IP address tied to a particular MAC address - if the clients MAC address matches an address specified by a reservation, the reserved IP address is then leased, rather than the scope address.
	- **Exclusions:** Is one or more IP addresses excluded from the IP address range, i.e. if the scope ranges from `192.168.1.1` to `192.168.1.100`, you can exclude the addresses `192.168.1.1` through to `192.168.1.10` for static IP assignment.
## Benefits of DHCP server
Some benefits include:
- In a large network, it can keep track of assigned addresses and to which machine they are assigned
- Computers can easily be moved and requested new IP configuration from a DHCP server on the network
- IP lease time can be controlled
- IP addresses can be reusable for other computers
DHCP uses UDP, so server are usually located on the same network and DHCP messages are hence short.
# DHCP Lease Process
1. During the boost process, a DHCP client **broadcasts** a `DHCPDISCOVER` message that its looking for a DHCP server
2. The DHCP server reserves an IP address for the client and makes a lease offer by sending a `DHCPOFFER` message to the client via **unicast**
3. The client responds with a `DHCPREQUEST` message via **broadcast** to accept the offered IP address
	- If serval DHCP servers respond to the request the client accepts the first offer that it retrives
4. The DHCP server whose offer was accepted responds with a `DHCPACK` message via **unicast**
	- It acknowledges the lease acceptance and contains the client's IP address lease and other IP addressing information 
![[Pasted image 20230903110107.png|centre|400]]
# DHCP Lease Renewal Process
After an address is leased:
- A record of the lease is stored in a database, including a lease expiration time
- When 50% of the lease time has elapsed, the computer attempts to renew the lease from the same DHCP server that originally responded
- If no response, the computer waits until the lease reaches 87.5%, a **broadcast** DHCP renewal request is sent
	- If no response when lease expires, the computer **broadcasts** a DHCP request for a new IP address
