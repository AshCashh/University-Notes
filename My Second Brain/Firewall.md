#networks
A firewall is a hardware device or software program that inspects packets going into or out of a [[Networks|Network]] or computer, and then discards or forwards packets based on a set of rules.
# Firewall Types:
## Hardware vs Software
A firewall is a hardware device software or a combination of both. 
- Hardware Firewall: A dedicated device with two or more network interfaces typically placed between a corporate [[LAN, WAN, MAN|LAN]] and the WAN connection
- Software Firewall: An individual device running on the [[Operating Systems|OS]]. Can either be host-based or personal
## Network-based Vs Host-based
- Network-based Firewall: Used to protect an entire private network, this firewall type is typically a dedicated hardware device
- Host-based Firewall: Used to protect a single host, this firewall type is typically software application
## Stateless Packet Filtering
Stateless packet filtering, also known as packet filtering is the filtering of network traffic based on the information in the IP header. Each packet is examined individually regardless of other packets that are part of the same session connection, e.g. [[Transmission Control Protocol#Establishing a Connection The 3-way Handshake|TCP 3-way Handshake]], [[File Transfer Protocol|FTP]].
## Stateful Packet Filtering
Stateful packet filtering operates the transport layer and monitors specific network protocol session messages across the network.
## Application-based 
An application based firewall operates at the application layer and inspects the context and content of packets against a defined set of rules. This firewall type learns application behaviours by observing how an application behaves over time, creating a baseline of normal behaviour.

This type of firewall is typically not used, as it is very resource intensive and can be difficult to maintain.

## Application Proxy
An application proxy firewall, also known as an application-layer gateway or application proxy is where connections are established through the proxy firewall. An external host sends a request to the proxy firewall, if the request is allowed, the proxy firewall establishes a connection to the internal host and forwards the request. When an internal host requests access to an external site, the proxy forwards the request on behalf of the internal host.

This type of firewall is also very resource intensive and can be difficult to maintain.