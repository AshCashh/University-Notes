---
alias: NIC
---
#cs
A Network Interface Card (NIC) is an add-on card plugged into a motherboard expansion slot that provides a connection between the computer and the network medium. Network cards can either be wired or [[Wireless]].

Although NICs are typically built into the motherboard, they can come as separate adapter cards that slide into one of the motherboard expansion slots.
![[Pasted image 20230728171323.png|centre|300]]
## NICs and MAC Addresses
A NIC has the important function of giving a computer a MAC address, NIC manufactures ensure that every MAC address is unique and stored in ROM (nonvolatile memory). 

The MAC address is composed of two 24-bit numbers:
- A 24-bit manufacturers ID called an organisationally unique identifier (OUI)
- A 24-bit serial number assigned by the manufacturer 
The address is expressed in hexadecimal notation usually as six, two-digit alphanumeric characters separated by dashes or colons (e.g. 04-40-31-5B-1A-C4). Valid hexadecimal digits should be followed by letter from a-f, A-F, and 0-9.

A frame with a destination MAC address composed of all `1s` or `FFs` is a broadcast frame / broadcast address.

## [[Wireless]] NICs
Wireless NICs must be chosen according to the type of wireless AP thats installed. Most are typically described as `802.11ac`, `802.11ax`, `802.11ax-2021` or `802.11`a/b/g/n. The letters a, b, g, n, ac, ax refer to the wireless networking standard the device supports.

Wireless NICs connect to networks using Service Set Identifiers (SSIDs). You are often prompted for a security key or a username and password, depending on the network's security configuration. 

## NIC Functions
Incoming messages:
- Receives bit signals and assembles them into frames
- Verifies the destination address
	- If the destination MAC address equals its own MAC address or broadcast address
- Removes frame header and sends the resulting packet to the network protocol.
Outgoing message:
- Receive packets from the Network layer
- Creates frames by adding MAC addresses/error check
- Converts frame into bit signals suitable for the medium and transmits them

## NIC Basics
![[Pasted image 20230728174146.png]]
![[Pasted image 20230728174200.png]]
