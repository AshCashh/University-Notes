#cs
UART or Universal Asynchronous Receiver-Transmitter is a simple and cost effective [[Serial Communication|Serial Communicating]] device. Instead, the sender and receiver must agree on a baud rate (the number of [[Binary|bits]] transmitted per second). This is typically in the range of 9600 baud to 115200 baud (with a 2Mbaud maximum).

UART is a frame based protocol, where each frame is signalled by a start bit (always LOW), and is fixed length and format. UART can be used in both [[Serial Communication#Serial Communication Terminology|Full-duplex]] or [[Serial Communication#Serial Communication Terminology|Half-duplex]], depending on the hardware implementation, where the transmitter and reciever are full independent. This means either a 1- or 2-wire mode is possible (plus 1 for GND).

## UART Frame Format
The UART frame format is as follows:
- Start bit: always LOW
- Data bits: 5 to 9 bits of data
- Parity bit: optional bit used to detect errors
- Stop bit: always HIGH
- Idle: in the idle state, the line is HIGH
![[Pasted image 20230506192044.png]]

The parity bit is used to detect errors in the data bits. It allows the reciever to detect a single-bit error in the frame. The parity bit can be configured to either be odd or even parity.
- For **even** parity, the total number of 1s in the data and parity bits must be even
- For **odd** parity, the total number of 1s in the data and parity bits must be odd
If a parity error is detected in a received frame, the receiver may choose to reject the frame.

## USART0 on the Attinty1626
The USART (Universal Synchronous/Asynchronous Reciever/Transmitter) peripheral is used to implement UART on the Attinty1626. The transmission operation is as follows:
1. The user loads the data for transmission into the `TXDATA` register
2. When the TX shift register is empty, the data will immediately be copied into the shift register
3. Data is shifted out from the TX shift register, one bit at a time, according to the baud rate.
4. The transmitter is double-buffered so that:
	- If a second byte is loaded into the `TXDATA` register before the first byte has finished transmitting, this byte will be transferred into the TX buffer and transmitted after the first byte
	- Additionally, writing a third byte will cause it to remain in the TXDATA register, until the previous two bytes have be transmitted
The reception operation is as follows:
1. The start of an incoming frame is detected based on the falling edge on the RX line
2. Data is shifted into the RX shift register, one bit at a time, accordng to the baud rate
3. Once the correct number of data bits have been shifted into the shift register, the data will be copied into the `RXDATA` register
4. The reciever is double-buffered so that:
	- If a second byte is shifted out the shift register before the first byte is read, it will be stored in the RX buffer
	- Additionally, a third byte will remain in the RX shift register until the RX buffer is empty
For more information about the USART0 peripheral, see the datasheet
### UART0 Configuration Example
```c
void uart_init(void) {
	PORTB.DIRECT = PIN2_bm; // Output enable TX pin
	USART0.BAUD = 1389; // 900 baud
	USART0.CTRLA = USART_RXCIE_bm // Enable RX interrupt
	USART0.CTRLB = USART_RXEN_bm | USART_TXEN_bm; // Enable RX and TX
}
```

## USART0
Configurable:
- Baud rate
- Number of data/stop bits
- Parity

#### TX Operation
User loads data for transmission into the `TXDATA` register. When the TX shift register is empty, the data will be copied into the shift register

Data is shifted out of the TX shift register one bit at a time, according to the selected baud rate and used to set TXD pin state. The hardware will automatically generate the required start, stop and parity bits per the user configuration

#### RX Operation
The start of an incoming frame is detected based on the falling edge of the RXD pin (start bit). Data is shifted into the TX shift register one bit at a time. Once the correct number of data bits have been shifted in, the data will be copied into the `RXDATA` register. The user will also recieve the parity and stop bits to confirm a valid frame. The received data can then be read from the `RXDATA` register

#### Buffering
Note that the USART peripheral is double buffered. Meaning there can be simultaneously:
- One frame actively being shifted in/out (in the TX/RX shift register)
- One frame in the TX/RX buffer
- One frame in the RX/TXDATA register
This means that throughput can be maximised as the gap between frames can be minimised and higher software latency can be tolerated before a recieve overflow.

#### Status and Error Handling
The `RXDATAH` register holds status information about a recived frame. Software can read this register to check for:
- Recieve complete
- Parity errors
- Frame errors (stop bits not set)
- Buffer overflow (receive data overwritten before being read by software)
Status information is also avaliable in the `STATUS` register. See data sheet 24.5.2.

#### Configuration
For normal UART operation only four registers need to be configured
- BAUD - baud rate
- CTRLB - transmitter and receiver enable
Optionally:
- CTRLA - interrupt enables 
- CTRLC - mode, parity, data width, stop bits

Default mode settings (CTRLC) are: asynchronous, 8-bit, no parity bit, 1 stop bit, see datasheet 16.3.3

Note that you will need to enable the corresponding TXD pin as an output and might need to select an alternate pin location via PORTMUX. Make sure enabling the transmitter/receiver is the final step.

#### Baud Rate
The value for the baud rate register is determined by your target bud rate and peripheral clock (CLK_PER) speed (same as CPU clock speed). Typical bud rates are: 9600, 19200, 38400, 57600, 115200.

Formula:
$$f_{BAUD}=\cfrac{64\times f_{CLK_PER}}{S\times BAUD}$$
where, S is the number of samples per bit:
- Asynchronous Normal mode: S = 16
- Asynchronous Double-Speed mode: S = 8
- Synchronous mode: S = 2

Example:
$$BAUD=\cfrac{64\times 3333333}{16\times 9600}=1389$$
Which is the value to load into the register to configure for the target BAUD rate

#### Example Configuration & Usage
```c
void uart_init(void){
	PORTB.DIRSET = PIN2_bm; // Enable PB2 as output (USART0 TXD)
	USART0.BAUD = 1389; // 9600 baud @ 3.3Mhz
	USART.CTRLB = USART_RXEN_bm | USART_TXEN_bm; // Enable TX/RX
}
uint8_t uart_getc(void){
	while (!(USART0.STATUS & USART_RXCIF_bm)); // Wait for data
	return USART0.RXDATAL;
}
void uart_putc(uint8 c){
	while (!(USART0.STATUS & USART_DREIF_bm)); // Wait for TXDATA to empty
	USART0.TXDATAL = c;
}
```
#### Polled vs Interrupt Driven
This example is a polled model for serial communication. Each time a byte is read/written, we poll the USART0 STATUS register:
- This is referred to as a blocking read/write, as the code does not proceed until read/write comples
- The delay may be significant for a slow serial interface (e.g. UART at 9600 baud)
- The CPU cannot do anything else until the read/write function returns

Alternatively, we can use interrupts to signal when the peripheral is read for new data to be read/written; this is an interrupt driven model for serial communication
- No delay is required as when an interrupt is triggered we are guaranteed that data is already ready to be read/written
- Read/write ISRs will always return in a deterministic amount of time
- The CPU can be doing other computations while the peripheral hardware is busy.

#### [[Interrupts|Interrupt]] Handling
![[Pasted image 20230508191836.png]]

Example
```c
void uart_init(void){
	PORTB.DIRSET = PIN2_bm; // Enable PB2 as output (USART0 TXD)
	USART0.BAUD = 1389;
	USART0.CTRLA = USART_RXCIE_bm | USART_DREIE_bm; // Enable DRE/RX interrupts
	USART0.CTRLB = USART_RXEN_bm | USART_TXEN_bm; // Enable TX/RX
}
ISR(USART0_RXC_vect) {
	*(rxbuf++) = USART0.RXDATAL; // Read new data into buffer
	if (rxbuf == RXBUFEND) USART0.CTRLA &= ~USART_RXCIE_bm; // Disable Interrupt
}
ISR(USART0_DRE_vect){
	USART0.TXDATAL = *(txbuf++); // Wrtie data out to UART
	if (txbuf == TXBUFEND) USART0.XTRLA &= ~USART_DREIE_bm; // Disable interrupt
}
```
Studio Example:
```c
void uart_initalise(void){
	PORTB.DIRSET = PIN2_bm; // Enable PB2 as an output
	USART0.BAUD = 1389; 
	USART.CTRLB = USART_RXEN_bm | USART_TXEN_bm;
}
uint8_t uart_getc(void){
	while (!(USART0.STATUS & USART_RXCIF_bm)); // Wait for data
	return USART0.RXDATAL;
}
void uart_putc(uint8 c){
	while (!(USART0.STATUS & USART_DREIF_bm)); // Wait for TXDATA to empty
	USART0.TXDATAL = c;
}
int main(void){
	uart_initalise();
	for (;;){
		uint8_t c = uart_getc();

		display_hex(c);
		uart_putc(c);
	}
}
```