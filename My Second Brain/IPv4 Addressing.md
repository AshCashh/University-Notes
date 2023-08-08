An [[Internet Protocol]] version 4 or IPv4 address consists of 32-bit numbers divided into four 8-bit values called "octets". Each octet can have a value from 0 to 255 and are separated by dotted decimals. For example, in the address `10.255.0.100`, 10 is the first octet and 100 the fourth octet.

## IP Address Classes
IP addresses are categorised in ranges referred to as Classes A, B, C, D or E. Only addresses in the A, B and C classes can be assigned to a network device (host). 

You can identify the class of a IP address by looking at the **first octet** and observing the following ranges:
- Class A: 1 - 126 
- Class B: 128 - 191
- Class C: 192 - 223

The following address ranges are IETF reserved for private networks and therefore cannot be routed across the [[Internet, Intranet, Extranet|Internet]]:
- Class A: 10.0.0.0 - 10.255.255.255
- Class B: 172.16.0.0 - 172.31.255.255
- Class C: 192.168.0.0 - 192.168.255.255

The `127.0.0.1` network is reserved for the loopback address, also referred to as the localhost. It is used to establish an IP connection to the same machine or computer being used by the end-user. Pinging this address will loop back to your own machine.

Today, IP addresses are considered classless addresses, where clients do not apply for a particular class of addresses. Instead, IP addresses are given from an Internet Service Provider (ISP). Most ISPs have already applied for a pool of IP addresses and then lease them to its clients.

![[Pasted image 20230805161653.png|500]]
#### Examples
Class A:
![[Pasted image 20230805162001.png]]
Class B:
![[Pasted image 20230805162506.png]]
Class C
![[Pasted image 20230805162700.png]]

- Valid host addresses only use numbers from 1-254

# Network Masking
Masking is a process that extracts the address of the physical network from an IP address. Usually when a router forwards packets from one network to another it uses this masking to identify if the packets belong to its network or not.


## Role of the Network Mask
A network mask determines which part of address denotes the network portion. Has 32-bits, 1 signifies the networking bits in the IP address. 0 signifies thee host bits in the IP address.
Default subnet mask for:
![[Pasted image 20230805175701.png|300]]
Can be represented in "slash" notation (e.g. "/16"). Address and network prefix may then be shown in a compact manner (`131.181.0.0/16`). The "/16" is the same as `255.255.0.0`. (16 bits)