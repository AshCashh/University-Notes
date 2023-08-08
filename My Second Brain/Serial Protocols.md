#cs 
A serial protocol is an agreed-upon standard by which two devices can communicate with each communicate with each other, enabling them to exchange data. [[UART]] and [[SPI]] are standards for transmitting through [[Serial Communication]].

## Requirements for a Serial Protocol
A serial protocol must:
- Able to recieve data during a transmission
- Able to recover from errors
- Engage in [[Flow Control]] 
- Be simple to implement / understand for both the transmitter and reciever

## Symbols
A symbol is the fundamental data type used in serial communication protocols, which can be comprised of several bits. THe number of bits is usually set by the underlying medium and depends on the [[UART#Baud Rate| Baud Rate]]. 

Smaller symbols are more flexible and allow for more symbols to be transmitted, whereas larger symbols are more efficient and allow for more data to be transmitted.

## Messages
If the information to be changed can be entirely encoded within a single symbol, there is no need for a message structure. However, more complex protocols require a message structure for large quantities of data or information of variable length. This is done by dividing the communication into discrete messages.

## Encoding
The choice of encoding may also be of concern, depending on the communication medium, symbol length, and other factors such as human readability. For example using the entire ASCII character set may not be desirable as it is not human readable. Human readable encoding schemes usually limit the number of symbols to a small subset of the ASCII character set:
- ASCII `32-126 (0x20-0x7E)` which uses 8-bit symbols
- Base64 `(0-9, A-Z, a-z, +, /)` which encodes 6-bits into an 8-bit symbol.
- Hexadecimal `(0-9, A-F)` which encodes 4-bits per symbol

## Message Structure
Messages typically contain the following information:
1. A start sequence to indiciate the beginning of a message
2. An identifier to indicate what type of message is being sent (if the protocol requires multiple message)
3. A payload containing the data specific to the message
4. A provision for escape sequences to allow for special characters (e.g., arbitrary data is not confused with start sequences)
5. A chechsum (or message digest), to ensure the integrity of the message
6. A stop sequence to indicate the end of a message

## Start Sequences
As a serial communication transmits a sequence of symbols with no structure, there is no guarantee that the entire message is recieved. To address this, a start sequence is used to indicate the beginnning of a message. The start sequence is usually a fixed number of unique symbols that do not appear in the payload, providing a synchronisation point. If payloads need to contain arbitrary sequences of symbols, escape sequences may be used.

## Multi-Symbol Start Sequences
While a single symbol start sequence is simple, a multi-symbol start sequence has potential benefits:
- Reduces need for escape sequences 
- Reduced likelihood of misinterpreting corrupted data as a start sequence

## Sub-Symbol Start Sequences
If a messages are encoded with fewer than 8 bits per symbol, the remaining bits can be used to encode a start sequence. For example, in UTF-8 encoding, the high bit is always cleared in the first byte of a sequence, while the high bit is always set in the remaining bytes.

## Message Identifiers
Serial protocols often have multiple categories of messages that may be transmitted. Commonly a fixed-length identifier is transmitted so that the reciever can respond with the appropriate action, or know when to expect a payload.

## Payloads
A payload is used when a message identifier alone is insufficient to convey the information required. Payloads should be as small as possible to reduce the overhead of the protocol, as longer payloads increase the risk of transmission errors, so it may be preferrable to split a large payload into multiple messages.

### Payload Length
Payloads may be of both fixed and variable length, depending on the protocol.
- For fixed length payloads, the message type itself may define the payload length and hence will know when to expect the end of the payload
- For variable length payloads, the payload length is encoded in the message itself, by either specifiying the length within the payload, or by using a delimiter to indicate the end of the payload.

### Variable Length Payloads
When variable length payloads are expected, two strategies are commonly used:
- Encode the payload length at the start of the payload, either with one or two symbols for (1-256) or (1-65536) bytes respectively.
- Use a sentinel to indicate the end of the payload. This is a special symbol that is not used in the payload, such as a null character
Note that the second strategy requires the reciever to be able to buffer the entire payload before processing it. If the payload is too large, this may not be possible

## Escaping Sequences
When there is potential ambiguity as to whether a given symbol or sequence of symbols is part of a sequence, a payload, or a sentinel for a payload, escape sequences may be necessary to handle certain characters.

In C, a backslash (\) is used to escape characters like the double quote (") to tell the compiler that the character is not the end of the string.

In serial protocol, this may not be appropriate as the backslash may be missed during transmission, and the next character may be treated as a start sequence for example. To address this, the escape sequence should not contain the symbol it is escaping. Instead, an alternate sequence is used to represent symbols when they are part of a payload or other contexts. Note that the escape sequence itself may be part of the payload, so it is important to also account for this.

## Handshakes
A protocol where the sender purely transmits data does not know whether the same information has been recieved and handled by the reciever. As such, it is common for protocols where only side is sending information and the other side recieving, to have the reciving side at least acknowledge what it has recieved (if the serial communications medium is half-duplex or full-duplex).

The most common form of handshakes are ACK and NACK messages (acknowledged and not acknowledged).
- ACK indicates that the message was recieved and that the contents were understood.
- NACK indicates that the message was recieved, but that there was an error in the message. For example, the message was malformed, failed its checksum, or was unable to be processed. In this situation, the sender may retransmit the message, or send a different message.

## Message Verification
As serial communciations are prone to transmission errors, it is important to verify that the message was recieved correctly. This is done by including a checksum in which the transmitter computes a value based on the contents of the message, such as the sum of the bytes, and transmits it with the message. The reciever then computes a similar checksum based on what it recieves and verifies that it matches the transmitted checksum.

This simple checksum detects may transmission errors however, it is not guaranteed to handle symbols send out of order, or symbols that are corrupt without changing the checksum.

## Flow Control 
When the reciever operates on little power or low storage, the sender may not be able to send data quicklym as the reciever may not be able to process it. Hence the sender may respond with a flow control message, such as WAIT, to indicate that it is currenlty processing the previous message, and RESUME when it is ready to recieve more data.

# Serial Protocol Parasing
Many serial protocols are designed to be simple to parse, due to the limited hardware or typical devices using serial communication. Howver, there are concersn around timing, state and buffers that need to be considered, especially when the device needs to do multiple thing at a time. For example, `scanf()` is flexible enought ot parse many simple message structures (if you can spare the program memory), it is a blocking function; highly undesirable in a controller that needs to be able to do other things at the same time.

## Timing Considerations
Other actions can be carried out at the same time as blocking operations through [[Interrupts]], for example, one of the TCBs could be used to generate regular interrupts so that other work can be done while waiting on blocking I/O operations. However, this would push the burden of maintaining state on the other work, and likely waste many CPU cycles unnecessarily. A better choice is to use the `UART_RX` interrupt to handle a single character at a time, then use a [[State Machines|State Machine]] to handle the parasing of the message. 

This state machine can be placed within the interrupt handler, or in a seperate function that is called in the main loop. The state machine can be implemented to consider the follow:
1. Idle: The paraser is waiting for a start sequence (and ignore all other symbols)
2. Start Sequence: The parser is reciving the start sequence
3. Message Identifier: The parser is receiving the message identifier
4. Payload: The parser is reciving the payload (could be separate states for various identifiers)
5. Checksum: The paraser is receiving the checksum.

### State Machine Solution
A state machine can be used to allow the data to be parsed as it is recieved.

Enumerate the different states that the decoder could be in:
- Before the start sequence has been encountered
- While receiving start sequence
- While receiving identifier
- While receiving payload (could have different state for each identifier, or store the identifier in a separate variable)
- While receiving checksum

![[Pasted image 20230522210002.png]]

```c
typedef enum{
	WAIT_START, 
	RECV_START,
	RECV_IDENT,
	RECV_PAYLOAD,
	RECV_CSUM
} serialstate;

typedef enum {
	LED_DISPLAY = 0x0E,
	PLAY_SAMPLE = 0x0F,
	DISPLAY_TEXT = 0x10
} messageid;

ISR(UART_RXC_vect){
	static serialstate state = WAIT_START;
	static uint8_t symbols_received = 0;
	static messageid mesg_id;
	static uint8_t payload[256];
	static uint8_t payload_len;
	uint8_t sym = USART0.RXDATAL;

	switch (state){
		case WAIT_START:
			if (sym == 'X'){
				state = RECV_START;
				symbols_recv = 1;
			}
			break;
		case RECV_START:
			if (sym == 'X'){
				symbols_recv++;
				if (symbols_recv == 4){
					state = RECV_IDENT;
				}
			}
			else {
				// Invalid start seq
				state = WAIT_START;
			}
			break;
		case RECV_IDENT:
			mesg_id = sym;
			state = RECV_PAYLOAD;
			symbols_recv = 0;
			switch (sym){
				case LED_DISPLAY:
					payload_len = 2;
					break;
				case PLAY_SAMPLE:
					payload_len = 64;
					break;
				default:
					// Invalid identifier
					state = WAIT_START;
					break;
			}
			break;
		case RECV_PAYLOAD:
			payload[symbols_recv++] = sym;
			if (symbols_recv == payload_len){
				state = RECV_CSUM;
			}
			break;
		case RECV_CSUM:
			uint8_t csum = 0;
			for (uint8_t i = 0; i < symbols_recv; i++){
				csum += payload[i];
			}
			state = WAIT_START;
			if (csum != sym){
				// Invalid checksum
				return;
			}
			switch (mesg_id){
				case LED_DISPLAY:
					led_display(payload);
					break;
				case PLAY_SAMPLE:
					play_sample(payload);
					break;
			}
			break;
	}
}

```

## Studio Demo
```c







```