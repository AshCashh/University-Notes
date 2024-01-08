#networks 
Network security can mean different things to different people. To [[Networks|Network]] users, network security is sometimes considered a necessary evil that takes the form of hard-to-remember passwords that must be changed frequently and cryptic terms, such as VPN and IPsec to describe methods they use to access the network. To other users, network security means the comfort of knowing that if they erase their hard drives accidentally, a network administrator will gladly restore their data from the most recent system backup.
# Cyber Security Terms
- **Vulnerability**: A weakness is a system, application or network that is subject to exploitation or misuse. 
- **Threat**: A potential cause of an incident, that may result in harm of systems and organisations.
- **Risk**: The likelihood of a threat exploiting a vulnerability to breach security or cause harm.

# [[Internet Protocol|IP]] Protocol Features
**Best Effort Delivery**:
- IP does not guarantee delivery of packets, this functionality is left up to a higher layer. If a packet is lost, it is lost
- The network has variable delays. This means that any packet sent in a specific order will net necessarily arrive in the same order
**Connectionless**: 
- Each packet is individually addressed and routed rather than a connection being established between the source and destination pre sending. This means it's possible for two packets from the same source to take separate paths to the destination.
**[[Routers & Routing|Routing]]**:
- Packets usually go through a series of routers before they can reach their destination. At each node in the network, the packet is examined and a decision is made on how to route the packet to the next node.
**Quality of Service (QoS) Control**:
- QoS is a feature of IP that allows the network to prioritise traffic. This is done by assigning a priority to each packet.

## IP Spoofing/DoS
Due to IPv4 not having security features, it's possible for an attacker to send packets/datagrams from a false source address to disguise itself.

Denial of Service (DoS) attacks are a type of attack where an attacker floods a network with traffic that appears to be from a legitimate source IP address to prevent legitimate users from accessing the network.

# [[Transmission Control Protocol|TCP]] Threats
**TCP SYN Flood**: A type of DoS attack where an attacker sends a large number of TCP SYN packets to a server to consume the servers resources and prevent legitimate users from accessing the server.
**Predicting TCP Sequence Numbers**: An attacker can predict the sequence numbers of TCP packets by sending a large number of TCP SYN packets to a server and observing the sequence numbers of the SYN/ACK packets sent back. If an attacker can predict both the sequence numbers of an ongoing communication session it can carry out an injection attack to insert corrupted or malicious data into the session.

# [[Domain Name System|DNS]] Threats
Due to the DNS scheme not containing any authentication or integrity checks, it's possible for a number of attacks to be carried out against DNS servers.
- **DNS Cache Poisoning**: An attack can poison the DNS cache of a client by sending a malicious DNS response to the client. This response will contains a false IP address for a domain name that the client is trying to access. The client will then cache this false IP address and will be unable to access the legitimate domain name. This can also allow the attacker to redirect the client to a malicious website.
- **DNS Flood**: An attacker can flood a DNS server with a large number of DNS requests to consume the servers resources and prevent legitimate users from accessing the server.

# Security Attacks
There are two types of attacks:
1. **Passive**: An attacker does not attempt to modify or destroy data, they simply observe the network traffic to gain additional information
2. **Active**: An attacker attempts to modify or destroy data. This can be done through a number of methods: masquerading, replay, modification, insertion, deletion, DoS and more.