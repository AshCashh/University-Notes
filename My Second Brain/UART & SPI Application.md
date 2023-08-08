#cs
[[UART]] and [[SPI]] applications on the QUTy. How to virtual COM port via USB-UART bridge and controlling the 7-segment display

## Virtual COM port via USB-UART bridge
The CP2102N is a USB-UART bridge
- On the USB (host, e.g. computer) side it presents as a Virtual COM Port (VCP)
- On the microntroller side it presents as a UART interface
- The VCP can be configured by the host to a specific UART specification (baud rate, parity, stop bits, etc)

By default, the PlatformIO serial monitor uses 9600 baud, no parity, 1 stop bit. Whatever bytes you write via the UART will be available to read via the VCP, and vice versa. Note that the TX pin (output) of the microcontroller is connected to the RX pin (input) of the CP2102N and vice versa.

## Controlling the 7-segment display
The 7-segment display on the QUTy is interfaced to the microcontroller by a 74HC595 shift register:
- A shift register is a device which translate a serial input or output into a parallel input or output
- On the QUTy it takes a serial, 1--bit output from the microcontroller and uses this to control, in parallel, the 7-segments on the LED display, plus a digit select signal (8 bits total)

The 74HC595 takes a clocked serial data stream as an input. this makes it a perfect candidate for interfacing via SPI, which produces:
- A 1-bit serial data output
- A corresponding clock

### 7-segment display via SPI
Q0-Q6 of the shift register control the 7 segments of the display. Q7 controls where the LHS or RHS digit is selected. 

If you clock a total of 8 bits out of the microcontroller via SPI:
- The first bit clocked out of the microcontroller (and into the shift register) will set the state of Q7
- The last bit clocked will set the state of Q0
Whether the LSB or MSB of the data is clocked out first depends on the DORD bit setting for your SPI configuration

To latch the data shifted into the shift register into the output register (and consequently update the state of Q0-Q7) a rising edge on the DIS LATCH net is required.

## Time Multiplexing
Only one side of the 7-segment display can ever be lit at a time. If we want both digits to be lit simultaneously, we need to rapidly switch between sides of the display:
- If this is done rapidly enough it will appear as both sides of the display are on
- Exactly as if we were [[Pulse Width Modulation|pulse width modulating]] the display to control the brightness

This is referred to as time multiplexing; each side of the display is given a slice of the total time. We should aim for 50% duty cycle for both display sides to achieve equal brightness.

This is fairly trivial to achieve using SPI; we write a new byte to the shift register at fixed intervals, each time swapping which digit we display. If we want to display independent digits, we need to hold the state of each digit and which digit should be sleected next so we can make the appropriate update.

Example:
```c
// Bytes latched onto 7-segment display
volatile int8_t left_byte = DISP_0 | DISP_LHS;
volatile int8_t right_byte = DISP_0;

// Current display side (alternates between left and right)
volatile uint8_t current_display_side = 0;

// 10ms interrupt
ISR(TCB0_INT_vect){
	if (current_display_side) == 1)
		SPI0.DATA = left_byte;
	else 
		SPI0.DATA = right_byte;

	// Toggle display side (flip LSB)
	current_display_side ^= 1;

	TCB0.INTFLAGS = TCB_CAPT_bm;
}

ISR(SPI0_INT_vect){
	// Latch the digit
	PORTA.OUTCLR = PIN1_bm; // Drive High
	PORTA.OUTSET = PIN1_bm; // Drive back to LOW

	// Clear the interrupt flag
	SPI0.INTFLAGS = SPI_IF_bm;
}
```
This display is updated by writing to the variables `left_byte` and `right_byte`.



## Two-digit, Time-multiplex display
This is a good canidate for intrrupt-driven programming. We need to make regular updates to the display (at say > 50Hz). 
- This will have to happen continously, so a delay loop is infeasible if we are going to anything else in our prgramme.
- LSH and RHS digits should be displayed for equal times, so the display update process is time critical
- A good application for periodic [[Interrupts]] from a timer

The actual serial communication process can be handled by the SPI peripheral. We just need to trigger regular SPI writes by loading data into the DATA register

Each time a new byte has been written to the shift register, we need to update its ouputs by generateing a rising edge on the DIS LATCH signal. We can use interrupts from the SPI peripheral to trigger this.

Suggested programme architecture:
1. Configure a timer to produce period interrupts, corresponding to double the inteded display refresh rate (e.g. 50Hz -> 20ms period, so choose 10ms interrupt interval)
2. Configure PORT pins and the SPI peripheral so that it can write data into the shift register
3. Configure an interrupt to occur when an SPI write is complete 
4. Declare global variables to hold the state of the two digits and currenlty selected digit
5. Write an ISR to handle the periodic interrupt; this ISR should trigger an SPI write, and each time the ISR executes should alternate which digit is displayed
6. Write an ISR to handle the SPI write complete interrupt; this ISR should produce a rising edge on the DISP LATCH net to update the shift register outputs Q0-Q7