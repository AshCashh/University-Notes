---
alias: OSI
tags: [cs, networks]
Created: 2023-07-25T10:53:06+10:00
Modified: 2024-07-03T19:35:33+10:00
---
The Open Systems Interconnection Model (OSI Model) is a conceptual model from the International Organisation for Standardisation (ISO) that provides a common framework for developers and students of [[Networks|Networking]] to work with and learn from. It is not specific to any protocol suite and can be applied to most networking protocols. It's also well known and acknowledged as the baseline for categorisation of [[Network Communication]] functions. 
# Structure of the OSI Model
The structure consists of a seven layers organisation of how data travels from place to place on any given network. Each layer provides services to the next higher layer until it reaches the application layer.
![[Pasted image 20230725110150.png]]

## Application Layer
The Application layer provides interfaces for applications to access network services (file sharing, message handling and data access). Common protocols found at the application layer include [[Hypertext Transfer Protocol]] (HTTP), [[File Transfer Protocol]] (FTP), and [[E-Mail Protocols]] (SMTP). Possible problems at this layer include missing or misconfigured client or server software and incompatible or obsolete commands used to communicate between a client and server.

## Presentation Layer
The Presentation layer handles data formatting and translation. 
- **For outgoing message**: converts data into a format specified by the application layer
- **For incoming messages**: reverses the conversion if required by the receiving application
Encryption/Decryption can be done at this layer.

## Session Layer 
The Session layer permits two computers to hold ongoing communications, called "sessions". This layer handles communication setup ahead of data transfers and session teardown when the session ends. Common network function include: name lookup, user logon and logoff. 

Manages the mechanics of on going conversations such as identifying which side can transmit data when and for how long. The session layer also provides for [[Serial Communication#Serial Communication Terminology|Full-duplex]], [[Serial Communication|Half-duplex]] or [[Serial Communication|Simplex]] operation and establishes procedures for Checkpointing is performed at this layer (e.g. keeping the audio in sync with video).

## Transport Layer
The Transport layer manages data transfer from one application to another across a network, done by breaking data down into smaller chunks called "segments". Segmenting data is important because every network technology has a maximum frame size called the maximum transmission unit (MTU). Includes [[Flow Control]] and acknowledgements to ensure reliability. Handles re-sequencing segments into the original data on receipt. 

The layer is responsible for end-to-end communications, often acts as an interface between the application and lower layers. It includes two protocols: 
- [[Transmission Control Protocol]]: A connection-oriented protocol and is designed for reliable transfer of information 
- [[User Datagram Protocol]]: A connectionless protocol and is designed for efficient communication of generally small amounts of data
Both protocols perform the following tasks:
- Work with segments (TCP) or datagrams (UDP)
- Provide a means to identify the source and destination application involved in a communication
- Protect data with checksum
### Segments and Datagrams
As discussed, TCP works with **segments** and UDP works with **datagrams**. For outgoing data, in which the Application-layer protocol requires the services of a Transport-layer protocol, the Application layer passes data to TCP or UDP, depending on which protocol it was designed to use.

Both TCP and UDP add a header to the data, the Transport layer protocol then passes the segment or datagram to the Internetwork-layer protocol (usually IP). 
### Identifying Source / Destination Applications 
The Transport layer header provides the information needed to determine the application to which the received data is sent. TCP and UDP use a **port number** to specify the source and destination Application layer protocols to which an Internet or other network message is to be forwarded when it arrives at a server. The port number is a 16-bit integer that is put in the header appended to a message unit. 
### Protecting Data with a Checksum
To protect data integrity, TCP and UDP provide a **checksum** similar to the Cyclic Redundancy Check (CRC). Intermediate devices (nodes) don't recalculate the checksum in the Transport layer, so if data corruption occurs during transmission, the final receiving host detects the checksum error and discards the data.
##### Transport Example
![[Pasted image 20230725112433.png|500]]
![[Pasted image 20230725112441.png|500]]

## Network Layer
The Network layer performs logical addressing, maps between logical network addresses (IP addresses) into physical addresses, performs routing (i.e. selects the best path) [[Routers & Routing|Routers]] operate at this layer.

This layer is where IP [[Network Communication#Software Component|Protocols]] operate and is the heart of the [[Transmission Control Protocol & Internet Protocol Suite|TCP/IP]] protocol suite. Protocols related at this layer include: [[Internet Protocol]] (IP), [[Address Resolution Protocol]] (ARP), [[Internet Control Message Protocol]] (ICMP) and IPsec. 

This layer is responsible for four main tasks:
- Defines and verifies IP addresses
- Routes packets through an internetwork 
- Resolves MAC addresses from IP addresses
- Delivers packets efficiently

Problems that can occur at the Network layer include: 
- Incorrect IP addresses or subnet masks
- Incorrect router configuration
- Router operation errors
## Data Link Layer
The Data Link layer works with frames and is the intermediary between the Network and Physical layer. It defines how computers access the network medium, Media Access Control address is defined at this layer. A frame consists of both a header and a trailer. Trailer component is labeled "FCS" (Frame Check Sequence) and contains a Cyclic Redundancy Check (CRC) code (a CRC is an error-detecting code commonly used in network communications).

The software component operating at this layer is in the [[Network Interface Card]] (NIC) driver. Hardware components that operate are the NICs and switches. Problems at this layer include collisions and invalid frames. These can be caused by collisions, poor network design, environmental interferences, line noise or NIC driver problems

## Physical Layer
The Physical layer converts bits into signals for outgoing messages and signals into bits for incoming messages. Wire media uses electrical pulses, fiber-optic uses light pulses and wireless media uses radio waves. Details for creating a physical network connection are specified at this layer (type of connectors used to attach the medium to the NIC.)

[[Serial Protocols#Encoding|Encoding]] (representing 0s and 1s by a physical signal) happen at this layer. Components at this layer include all the cable and connectors used on the medium, repeaters and hubs (old technology).

Problems occurring here are often related to:
- Incorrect media termination
- Electromagnetic interference or noise that scrambles the signals 
- NICs and hubs are misconfigured or malfunctioning
