#cs
A computer [[Networks|Network]] consists of two or more computers connected by some kind of transmission medium (such as cable or airwaves). In order to access the internet, a computer has to be able to connect to a network. Communication protocols may be implemented by [[Hardware]], [[Software]], or a combination.

## Network Connectivity
Network connectivity or network topology is the means by which individual terminals, computers, mobile devices and [[LAN, WAN, MAN|LAN]] connect together. There are many network topology layouts:
1. **Peer-to-Peer**: one in which two or more computers share files and access one another. Done either wireless or wired 
2. **Star Topology**: one in which every host in connected to a central hub (either an access point or switch).
3. **Ring network**: one in which each node is connected to its left and right neighbour node.

## Hardward Component
Networking hardware, also known as network equipment or computer networking devices are electronic devices which are required for communication and interaction between devices on a network.

Some core networking components:
- **[[Network Interface Card]] (NIC)**
- **Network Medium**: is the existent path or physical channel used for transmission in the network. An [[Ethernet]] cable is used to attach to the NIC of a computer for wired connections. Wireless NIC translates data into radio signals and then transmits via antenna's for wireless connection.
- **Interconnecting Device**: Allows two or more computers to communicate on the network without being directly connected to one another:
	- **Router**: a networking device that forwards data packets between computer networks. Used for connecting multiple networks together.
	- **Switch**: a device for connecting multiple computers within a network, uses packet switching to receive, process and forward data to the destination device. 
	- **Access Point (AP)**: Allows wireless devices to connect to a [[Wireless]] network

#### Difference between a Router and Switch
A switch is used for connecting devices in a network. While a router connects networks together. A router links computers to the internet, so that users can share the connections. It also acts as a dispatcher, choosing the best path for information to travel.

## Software Component 
- **Network Clients and Servers**: network client software requests information stored on another network computer or device. Network server software allows a computer to share its resources.
- **Protocols**: Set of rules for exchanging information such as format. Examples include: [[Internet Protocol Suite]], IEEE 802, Ethernet.
- **NIC Driver**: Receives data from protocols and forwards this data to the physical NIC.
- **Subnet Mask:** Is used by the TCP/IP protocol to determine whether a host is on the local subnet or on a remote network
- **Default Gateway:** A router that is specified on a host, which links the host's subnet to other networks.

## Steps of Network Communication
1. Application tries to access a network resource by sending a message
2. Client software formats the message and passes the message on to the network protocol
3. Protocol packages the message in a format suitable for network and sends it to the NIC driver
4. NIC driver sends data in the request to the NIC card to be converted into necessary signals to be transmitted to the network 

### Layers of the Network Communication Process
Each step required for a client to access network resources is referred to as a layer. Each layer has a task and all layers work together.
![[Pasted image 20230724230139.png]]
 
