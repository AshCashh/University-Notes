#cs
In [[Telecommunications]], serial communication is the process of transmitting data one [[Binary|Bit]] at a time. In contrast to parallel communication, where several bits are sent as a whole, on a link with several parallel channels.

On a [[Microprocessors & Microcontrollers|Microcontroller]], this is typically done via a digital I/O pin. 
The form of serial communication is determined by the protocol used (how the the data is arranged, timing, etc.) and the physical interface used (voltage level used to represent bits). For two devices to communicate, they must both use the same protocol and physical interface

## Serial Communication Terminology
- **Transmit**: To send data. Often abbreviated to Tx
- **Receive**: To receive data. Often abbreviated to Rx
- **Full-duplex**: Bidirectional communication, occurring simultaneously
- **Half-duplex**: Bidirectional communication, occurring in one direction at a time
- **Simplex**: Unidirectional communication
- **Synchronous**: Communication relaying on a shared clock
- **Asynchronous**: Communication that does not rely on a shared clock
There are many serial interfaces used in embedded systems, including:
- **[[UART]]**: Universal asynchronous receiver/transmitter
- **[[SPI]]**: Serial peripheral interface
- [[I2C]]: Inter-integrated circuit
- **[[CAN]]**: Controller area network
- $\mathbf{I}^2$**S**: Inter-IC sound

## DTE vs. DCE Devices
A serial link is a point-to-point link between two devices. Devices that communicate over a serial interface are divided into:
- **Data Terminal Equipment (DTE)**: An end instrument that converts user information into signals or reconverts received signals. 
- **Data Communications Equipment (DCE)**: Typically, a modem or other piece of data communications equipment.

When connecting two DTE (such as two routers in the lab) devices together without a modem, you require a special type of cable called a null modem.

Generally, DCE devices provide the clock rate and the DTE device synchronises on the provided clock rate.
![[Pasted image 20230727223540.png|500]]