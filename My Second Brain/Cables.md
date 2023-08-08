#cs
## Types of Cables
### Coaxial Cable 
Coaxial cable or "coax" for short was the predominant form of networking cabling. 
- Inexpensive and easy to install
- Phased out in the early 1990s
- Now primarily used in connecting a cable modem to the wall outlet your cable TV/Internet provider installs

### Twisted-Pair Cable
Twisted-pair (TP) cable comes in two types: 
- Unshielded Twisted-Pair (UTP)
- Shielded Twisted-Pair (STP)
TP cable is classified by category:
- TP is Category 1-8, although categories 1, 2 and 4 and nearly obsolete
- Categories 5e, 6 and 7 UTP cabling are the most popular types of UTP
- Twists are necessary to improve resistance to crosstalk from wires and EMI from outside sources
Summary: 
- Most common form of wire
- Relatively inexpensive and easy to install
- Carries high data rates (but not the highest)
- Can suffer from electromagnetic noise and easily wire-tapped
![[Pasted image 20230727205304.png|400]]

### Shielded Twisted-Pair Cable
Shielded Twisted-Pair cable (STP) includes shielding to reduce crosstalk and limit the effects of external interference. 
- Has a wire braid inside the sheath material or a foil wrap
- Best to use in electrically noisy environments or very high-bandwidth applications
![[Pasted image 20230727205232.png|300]]

### Twisted-Pair Cable Plant Components
A twisted-pair cable plant requires more than just the cabling, which is usually sold in spools of 1000 feet. 
- RJ-45 Connectors - STP and UTP uses registered jack 45 (RJ-45): Mostly used in patch cables, which are used to connect computers to hubs, switches and wall jacks.
![[Pasted image 20230727205547.png|300]]
- Patch cable: A short ethernet cable for connecting a computer to an RJ-45 jack or connecting a patch-panel port to a switch or hub (router).
![[Pasted image 20230727205937.png|300]]
- RJ-45 Jacks: What you plug an RJ-45 connector into
![[Pasted image 20230727210105.png|300]]
- Patch Panels: Used to terminate long runs of cable from computers to the wiring closet (location of switches)
![[Pasted image 20230727210226.png|300]]
- Distribution racks: Used to hold network equipment, such as routers, switches and patch panels.
![[Pasted image 20230727210334.png|300]]

## Installing UTP Cabling 
Cable termination: putting RJ-45 plugs on the ends of cable or punching down wires into terminal blocks on a jack or patch panel.
Tools needed: Wire cutters, crimping tool, cable tester, punchdown tool, cable stripper

When making a cable or terminating a cable it is important to get the coloured wires arranged in the correct order.
Two standards: 568A and 568B 
![[Pasted image 20230727210740.png|400]]

## Straight-Through vs Crossover Cable
When making standard patch cable, you use the same wiring standards on both ends of the cable so each wire is in the same corresponding location on both ends of the cable (pin 1 goes to pin1, etc). This type of cable is called a straight-through cable.

The crossover cable, uses the 568B standard on one end and 568A on the other. This arrangement crosses the transmit and receive wires so that transmit signals on one end connect to receive signals on the other end. This type is often needed when you connect two devices of the same type to one another, e.g.
![[Pasted image 20230727212807.png|300]]
![[Pasted image 20230727212852.png|400]]

Crossover is used to connect:
- PC to PC, PC to router, router to router, hub to hub, switch to switch
Straight through is used to connect:
- PC to switch, PC to hub, switch to router

### Do we still need a crossover cable?
Nowadays, the need for crossover cables has been eliminated with latest equipment. G/Ethernet comes with automatic medium-dependent interface crossover (Auto-MDIX). This technology detects whether you need a crossover cable or a straight-through cable and automatically configures the network interface card accordingly. Yet we still need to use crossover cables to connect two devices of the same type, e.g. router to router, switch to switch.

## Fiber-Optic Cable 
Fiber-optic cabling uses extremely thin strands of glass to carry pulses of light long distances and at high data rates. It's typically used in inter networks to connect switches and routers and sometimes to connect high-speed servers to the network.

### Composition: 
- A slender cylinder of glass fiber called the core is surrounded by a concentric layer of glass called the cladding
- Fiber is then jacketed in a thin transparent plastic material called the buffer
![[Pasted image 20230727214345.png|300]]

Bits are transmitted as pulses of light instead of electricity. Information is sent in a beam of light bouncing down a glass or plastic pipe. Fiber-optic has less attenuation and hence carries signals over a much longer distance with a repeater compared to copper.

### Installation 
- More difficult and time consuming than copper media installation 
- Connectors and test equipment required for termination are still more expensive than copper

### Fiber-Optic Cable Types
Fiber-optic cables come in two main types: 
- Single-Mode Fiber (SMF): 
	- Includes a single, extremely small diameter fiber at the core (8 microns)
	- Generally uses laster light source
	- Spans the longest distances 
	- Used in higher-bandwidth applications
- Multimode Fiber (MMF): 
	- Larger diameter fiber at the core (50 and 62.5 microns)
	- Costs less than SMF
	- Use LED for light source 
	- Spans shorter distances

### Summary
- Fiber optic cable carry the highest data rate for the longest distances
- Initial cost-wise is more expensive than twisted pair and coaxial 
- Considering the superiority of fiber, initial costs outweighed by capacities
- Not affected by electromagnetic noise 
- Cannot be easily wiretapped

## How are Cables used?
NBN Fixed Line Connections:
- Fibre to the Premises (FTTP)
- Fibre to the Building (FTTB)
- Hybrid Fibre Coaxial (HFC)
- Fibre to the Curb (FTTC)
- Fibre to the Node (FTTN)
NBN Fixed Wireless/Satellite:
- NBN Fixed Wireless
- Satellite
![[Pasted image 20230727220350.png|600]]
