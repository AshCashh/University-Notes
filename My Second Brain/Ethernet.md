#cs
Ethernet is a family of wired computer networking technologies commonly used in [[LAN, WAN, MAN]]. It was introduced in 1980 and standardised in 1983 as IEEE 802.3. The protocol has evolved and improved over time to transfer data. The system now has three main speeds: 10Mbps, 100Mbps and 1Gbps. 

Although there are many variations of Ethernet, all forms are similar in their basic operation and frame formatting. What differs in variations are the cabling, speed of transmission and method by which bits are encoded on the medium. Because frame formatting are the same, Ethernet variations are therefore compatible with on another. Hence why [[Network Interface Card]] and switches are described as 10/100 or 10/100/1000 devices. These devices can support multiple Ethernet speeds.

## Ethernet Frames
A frame is the unit of network information that NICs and switches work with. It's the NICs responsibility to transmit and receive frames and a switches responsibility to forward frames out the correct switch port to get the frame to its destination

Ethernet networks can accommodate frames between 64 bytes and 1518 bytes. Shorter or longer frames are considered errors. Each frame is composed of the following:
- A 14-byte header composed of these three fields:
	- 6-byte Destination MAC Address field
	- 6-byte Source MAC Address field
	- 2-byte Type field
- A Data field from 46 to 1500 bytes
- A frame trailer (Frame Check Sequence FCS) of 4 bytes
![[Pasted image 20230728185031.png]]

## Ethernet Media Access
Before a NIC can transmit data to the network medium, it must adhere to some rules governing how and when the medium can be accessed for transmission. The set of rules for each networking technology is referred to as its **media access method**.

The media access method that Ethernet uses in [[Serial Communication#Serial Communication Terminology|Half-Duplex]] mode is Carrier Sense Multiple Access with Collision Detection (CSMA/CD).
- **Carrier Sense**: Listen before send - must hear silence
- **Multiple Access**: If two or more stations hear silence, multiple stations may transmit at the same time
- **Collision Detection**: If two or more stations transmit, a collision occurs and is detected by the NIC; all stations must retransmit

## Ethernet Error Handling
One reason for Ethernet's low cost and scalability is its simplicity. It's considered a best-effort delivery system, meaning that when a frame is sent, theres no acknowledgment or verification that the frame arrived at its intended destination. Ethernet relies on network protocols like [[Internet Protocol Suite|TCP/IP]] to ensure reliable delivery of data.

Ethernet also detects whether a frame has been damaged in transit. The error-checking code in a frame's trailer is called a Cyclic Redundancy Check (CRC) (Handled in the [[Open System Interconnection#Data Link Layer|Data Link Layer]]). If a frame is detected as damaged, it is simply discarded with no notification.

## Ethernet Addressing
Every Ethernet has a physical MAC address, see [[Network Interface Card#NICs and MAC Addresses|NICs and MAC Addresses]] for formatting.

## Ethernet Standards
Ethernet standards expressed as:
- **X**Base**Y** - 10Base2, 10BaseT, 100BaseT, 100BaseFX. Where:
	- **X** - designates the speed of transmission
	- **Y** - specifies the type of media (T = twisted-pair, FX = fiber optic, L = long wavelength laser)
10BaseT (dated):
	- Uses two of the four wire pairs
	- Runs over Category 3 or higher UTP cabling
	- Highly susceptible to collisions and s obsolete
100BaseTX:
- A common variety 
- Runs over Category 5 or higher UTP
- Uses two of four wire pairs
- Two types of 100BaseTX hubs
- Switches can be used to interconnect multiple hubs
100BaseFX:
- Runs over two strands of fiber optic cabling 
- 100Mbps
- Typically used as backbone cabling between switches
- Also used to connect clients or servers when immunity to noise and eavesdropping is required
1000BaseT Ethernet:
- Known as "Gigabit Ethernet"
- Runs over Category 5 or higher UTP and uses all four wire pairs
10GBaseT Ethernet:
- Runs over four pairs of Category 6A or 7 UTP
- Operates only in full-duplex mode (send & receive)
- Still considered an expensive option
- Good for network servers so they can keep up with desktop systems that commonly operate at 1Gbps
![[Pasted image 20230728200710.png]]
![[Pasted image 20230728200719.png]]
