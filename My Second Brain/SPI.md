#cs
SPI or Serial Peripheral Interface is a synchronous [[Serial Communication]] protocol where the bitrate is defined by the SPI clock speed ranging from 10MHz to 20MHz. SPI is typically used for high-speed, inter-IC communications (communication with other peripherals) over short distances. SPI is alos [[Serial Communication#Serial Communication Terminology|Full-duplex]], and can be configured to use a 2-, 3-, 4-wire modes (plus 1 for GND). It can be used to communicate with multiple devices simulaneously, using chip select (CS or slave select) lines to select the device to communicate with. Typically in a master slave model, the master device controls the clock.

The SPI peripheral can be used to interface to devices that produce or consume a serial bit stream, clocked or otherwise. The clock phase and polarity can also be modified to suit the device being interfaced to. It is also possible to have multiple masters on the same bus, but this requires a careful mechanism to arbitrate access to the bus.
### SPI0 Configuration Example
```c
void spi_init(void){
	VPORTC.OUT = PIN0_bm | PIN2_bm; // Drive output to LOW on SPI CLK. and SPI MOSI
	VPORTC.DIR = PIN0_bm | PIN2_bm; // Output enable SPI CLK and SPI MOSI

	PORTMUX.SPIROUTEA = PORTMUX_SPIO_ALT1_gc;

	SPI0.CTRLB = SPI_SSD_bm; // Disable client select line
	SPI0.INTCTRL = SPI_IE_bm; // Enable SPI interrupts (to latch SPI DATA)
	SPI0.CTRL = SPI_MASTER_bm | SPI_ENABLE_bm; // Enable SPI as master
}
```
## Common SPI Applications
Interfacing microcontrollers to external peripherals
- Memory
- ADCs and DACs
- Displays
- LED drivers
- Shift registers
- Sensors

## SPI0 on ATtiny1626
Configurable:
- Host or client mode
- Data order
- Clock speed
- Clock phase
- Clock polarity

#### Configuration
Datasheet section 25.5

CTRLA:
- Master/client
- Data order
- Clock speed
- Enable
CTRLB: 
- Buffer mode enable
- Client select disable
- Clock mode

Remember to configure relevant pins as ouputs and alternative pin locations via PORTMUX if required

#### [[Interrupts]]
Normal mode:
![[Pasted image 20230508192744.png]]
Buffer mode:
![[Pasted image 20230508192803.png]]

#### SPI0 Configuration & Usuage
```c
void spi_init(void){
	PORTMUX.SPIROUTEA = PORTMUX_SPI0_ALT1_gc; // SPI pins on PC0-3
	PORTC.DIR |= (PIN0_bm | PIN2_bm); // Set CLK (PC0) and MOSI (PC2) as outputs

	SPI0.CTRLA = SPI_MASTER_bm; // Master, /4 prescaler, MSB first
	SPI0.CTRLB = SPI_SSD_bm; // Mode 0, client select disable, unbuffered
	SPI0.CTRLA |= SPI_ENABLE_bm; // Enable
}
void spi_write(uint8_t data){
	SPI0.DATA = data; // Note DATA register used for both TX and RX
}
uint8_t spi_read(void){
	return SPI0.DATA: 
}
```
![[Pasted image 20230509171551.png]]
```c

void spi_init(void){
	VPORTC.OUT = PIN0_bm | PIN2_bm; // Drive output to LOW on SPI CLK. and SPI MOSI
	VPORTC.DIR = PIN0_bm | PIN2_bm; // Output enable SPI CLK and SPI MOSI

	PORTMUX.SPIROUTEA = PORTMUX_SPIO_ALT1_gc;

	SPI0.CTRLB = SPI_SSD_bm; // Disable client select line
	SPI0.INTCTRL = SPI_IE_bm; // Enable SPI interrupts (to latch SPI DATA)
	SPI0.CTRL = SPI_MASTER_bm | SPI_ENABLE_bm; // Enable SPI as master
}
```
Studio Example:
```c
void timer_init(void){
	TCB0.CTRLB = TCB_CNTMODE_INT_gc; // Periodic interrupt mode
	TCB0.CCMP = 33333; // 10ms at 3.33Mhz
	TCB0.INTCTRL = TCB_CAPT_bm; // Capture interrupt enable
	TCB0.CTRLA = TCB0_ENABLE_bm; // Enable
}
void spi_init(void){
	PORTMUX.SPIROUTEA = PORTMUX_SPI0_ALT1_gc; 
	PORTC.DIRSET = (PIN0_bm | PIN2_bm);
	PORTA.OUTSET = PIN1_bm; // DISP_LATCH initially high
	PORTA.DIRSET = PIN1_bm;

	SPI0.CTRLA = SPI_MASTER_bm; // Master, /4 prescaler, MSB first
	SPI0.CTRLB = SPI_SSD_bm; // Mode 0, client select disable, unbuffered
	SPI0.INTCTRL = SPI_IE_bm; // Interrupt enable
	SPI0.CTRLA |= SPI_ENABLE_bm; // Enable
}
void spi_write(uint8_t data){
	SPI0.DATA = data; 
}
void main(void){
	cli();
	uart_init();
	spi_init();
	timer_init();
	sei();


	for (;;){
	
		uint8_t c = uart_getc();
		if (c == 'a'){
			digit1 = (digit1 == 9)? 0 : digit1 + 1;
		}
		if (c == 's'){
			digit2 = (digit2 == 9)? 0 : digit2 + 1;
		}
		uart_putc(c);
	}

}
voltatile uint8_t segs [] = {
	0x08,0x6B,0x44,0x41,0x23,0x11,0x10,0x4B
}
volatile uint8_t digit1 = 
volatile uint8_t digit2 = 
ISR(SPI0_INT_vect){
	// Create rising edge
	PORTA.OUTCLR = PIN1_bm;
	PORTA.OUTSET = PIN1_bm;
	SPI0.INTFLAGS = SPI_IF_bm;
}
ISR(TCB0_INT_vect){
	static int digit = 0;
	if (digit){
		spi_write(segs[9] | (0x01 << 7));
	}
	else{
		spi_write(segs[6]);
	}
	digit = !digit;
	TCB0.INTFLAGS = TCB_CAPT_bm;
}



```