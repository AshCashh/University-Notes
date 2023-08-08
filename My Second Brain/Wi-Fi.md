#cs
The 1997, 802.11 [[Wireless]] networking standard, also referred to as Wireless Fidelity (Wi-Fi) has continued to undergo development. With it, manufacturers of wireless networking devices have brought inexpensive, reliable wireless [[LAN, WAN, MAN|LANs]] (WLANs) to homes and businesses.

Essentially, 802.11 wireless is an extension to [[Ethernet]], using airwaves instead of [[Cables|Cabling]] as the medium, although most 802.11 networks incorporate some wired Ethernet segments.

## Wi-Fi Modes of Operation
Wi-Fi networks can operate in one of two modes:
- Infrastructure mode: Wireless stations that connect through a wireless access point (AP).
- Ad-hoc (peer-to-peer) mode: Uncommon wireless mode with no central device and data travels from device to device in a line.

## Wi-Fi Channels and Frequencies
Wi-Fi networks operate at one of two radio frequencies: 2.4 GHz and 5.0 GHz. However, 2.4 GHz is from 2.412 through to 2.484 divided into 14 channels spaced 5 MHz apart. 5.0 is 4.915 through to 5.825 GHz divided into 42 channels of 10, 20, 40, 80, 160 MHz each:
![[Pasted image 20230728204907.png]]

### 2.4 GHz vs 5 GHz
2.4 GHz: 
- Lower data rate, more susceptible to interference and as more devices using this spectrum
- Larger coverage area, better at successfully penetrating solid objects
5 GHz:
- Higher data rate, less susceptible to interference and usually has fewer devices using this frequency
- Smaller coverage area, less successful at penetrating solid objects

## Wi-Fi Standards
Current Wi-Fi standards include 802.11a, 802.11g, 802.11n and 802.11ac with speeds starting at 11 Mbps for 802.11b and up to more than 5 Gbps for some versions of 802.11ac.
![[Pasted image 20230728205114.png]]

## Wi-Fi Access Methods and Operation
Access Method:
- Sending station can't hear if another station begins transmitting so they cannot use the CSMA/CD access method that Ethernet uses
- Wi-Fi devices use carrier sense multiple access with collision avoidance (CSMA/CA)
- Optionally be used with request-to-send/clear-to-send (RTS/CTS) packets and acknowledgements

## CSMA/CA Protocol Steps
1. Sender node (A) has some data to transmit
2.  A checks if the media is free or not
3. Optionally, the sending node can send transmits an RTA packet to the AP
4. The sending node waits until all nodes have had time to receive the jam signal
5. AP replies with a CTS (Clear to Send) packet
6. During transmission, the node monitors the media for an RTS signal from any other node that may already be transmitting data. If an RTS signal is received, it stops transmitting and reties after a random delay

## Wi-Fi Security
Because the network signal and therefore the network data of a Wi-Fi network aren't constrained by physical media, access to a Wi-Fi network must be secure.
- Signals from a Wi-Fi network can travel several hundred feet, meaning Wi-Fi devices outside your home or business can detect them.
- Wi-Fi network should be protected by an encryption protocol that makes data difficult to interpret
- Wi-Fi devices support one of the following encryption protocols: 
	- Wired Equivalent Privacy (WEP) - **Very old and not secure.**
	- Wi-Fi Protected Access WPA - Not secure 
	- WPA2, WPA3 - Acceptable
	Although not all devices support all three protocols. Older devices may only support WEP and/or WPA