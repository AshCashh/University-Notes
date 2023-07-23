#cs
Serial communication is the process of transmitting data one bit at a time. On a [[Microprocessors & Microcontrollers|Microcontroller]], this is typically done via a digital I/O pin. 
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

