---
tags: [os]
Created: 2023-09-03T21:07:14+10:00
Modified: 2024-07-03T19:35:33+10:00
---
A distributed system is a collection of loosely coupled processors interconnected by a [[Network Communication|Communications Network]]. A distributed system can also be thought of as a collection of physically separate, possibly heterogeneous, [[Computer System|Computer Systems]] that are [[Networks|Networked]] to provide users with access to the various resources that the system maintains.
![[Pasted image 20230903211136.png|centre|400]]
Processors variously called nodes, computers, machines, hosts:
- Site is a location of the processor
- Generally a server has a resource a client node at a different site wants to use
# Reason for Distributed Systems
There are three major reasons for building distributed systems: 
- **Resource Sharing**: provides mechanisms for sharing files at remote sites, processing information in a distributed database, printing files at remote sites or using remote specialised hardware devices
- **Computation Speedup**: Allows the distribution of sub-computations among various sites, load sharing or job migration
- **Reliability**: Able to detect and recover from site failure, function transfer or reintegrate failed site.
- **Communication**: Able to message pass - all higher level functions of a standalone system can be expanded to encompass a distributed system

Computers can be downsized, more flexibility, better user interfaces and easier maintenance by moving from large systems to multiple smaller systems performing distributed computing.
# Network and Distributed Operating Systems
There are two general categories of network-oriented operating systems: network operating systems and distributed operating systems. Network OSs are simpler to implement but generally more difficult for users to access and use than distributed OSs, which provide more features
## Network Operating Systems
A network OS provides an environment in which users can access remote resources by either logging in to the appropriate remote machine or transferring data from the remote machine to their own machines. This is done explicitly by:
- **Remote Login**: Where logging into the appropriate remote machine is done by [[Telnet and Secure Shell|Telnet or Secure Shell]].
- **Remote Desktop**
- **Remote File Transfer**: Provide a mechanism for transferring files from one machine to another, done via the [[File Transfer Protocol]]. 

Users must change paradigms - establish a session, give network based commands to operation. Therefore it is considered more difficult for users in general.
## Distributed Operating Systems
Here users access remote resources in the same way they access local resources. Data and process migration from one site to another is done here and depending on the goals of the system, it can implement computation migration or process migration.
- **Data Migration**: Transfer data by transferring entire file or transferring only those portions of the file necessary for the immediate task.
- **Computation Migration**: Transfer the computation, rather than the data across the system. Done via remote procedure calls or messaging system
- **Process Migration**: Execute an entire [[Process]] or parts of it at different sites. Scheme may be used for the following reasons:
	- Load balancing: Distribute processes across the network to even workloads
	- Computational Speedup: Subprocesses can run concurrently on different sites
	- Hardware Preference: process execution may require specialised processors
	- Software Preference: Required software may be available at only a particular site
	- Data Access: Run process remotely, rather than transfer all data locally
Consider the World Wide Web