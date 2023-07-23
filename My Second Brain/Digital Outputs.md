#cs
Digital output interfaces are designed to be able to drive connected circuitry to one of states, high or low. However, the appropriate technique is context specific. When referring to digital outputs, we will refer to the states of a net. A **net** is defined as the common point of connection of multiple [[Circuit Elements]].

In this section we will consider:
- What kind of load(s) is the output required to drive?
	- High-impedance output (e.g. IC pint), LED, etc
- Could more than one device be attempting to actively drive the net to a specific logic level?
	- A fault bus where any number of devices could signal a fault
	- A half-duplex serial communication line