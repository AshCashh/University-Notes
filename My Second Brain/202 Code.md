---
Created: 2023-06-27T20:35:53+10:00
Modified: 2024-07-03T19:35:33+10:00
---
# Timers
#### TCB0 Initialisation 
```c
#include <avr/io.h>
#include <avr/interrupt.h>

void tcb_init(){
	cli(); // Disable interrupts
	TCB0.CTRLB = TCB_CNTMODE_INT_gc; // Configure TCBO in periodic interrupt mode
	TCB0.CCMP = 3333; // Set period to some value (3.33MHz)
	TCB0.INTCTRL = TCB_CAPT_bm; // Invoke the CAPT ISR when the counter reaches CCMP
	TCB0.CTRLA = TCB_ENABLE_bm; // Enable TCB0
	sei(); // Enable interrupts
}
ISR(TCB0_INT_vect){
	// This interrupt will execute every 1ms
	// do something
	TCB0.INTFLAGS = TCB_CAPT_bm;
}
```
#### TCA0 Initialisation 
Go to PWM

#### De-Bouncing 
```c
void pb_init(void){

	// PBs PB4-7, enable pullup resistors
	PORTA.PIN4CTRL = PORT_PULLUPEN_bm;
	PORTA.PIN5CTRL = PORT_PULLUPEN_bm;
	PORTA.PIN6CTRL = PORT_PULLUPEN_bm;
	PORTA.PIN7CTRL = PORT_PULLUPEN_bm;

}
volatile uint8_t pb_debounced_state = PIN4_bm;
volatile uint8_t pb_falling_edge = 0;
volatile uint8_t pb_rising edge = 0;

// Periodic 4ms interrupt
ISR(TCB0_INT_vect){
	// Two verticle counters for a total of 4 counter states
	static uint8_t counter0 = 0;
	static uint8_t counter1 = 0;

	// Capture the state of the pushbuttons from the port pin
	uint8_t pb_sample = PORTA.IN;

	// Detect a change in state 
	uint8_t pb_edge = pb_sample ^ pb_debounced_state;

	// Update counters
	// If the state of the pushbutton has changed, increment the counter
	counter1 = (counter1 ^ counter0) & pb_edge;
	counter0 = ~counter0 & pb_edge;

	// Save previous debounced state
	uint8_t pb_previous_state = pb_debounced_state;

	// Update debounced state if counter is 3 or immediately on falling edge
	pb_debounced_state ^= (counter1 & counter0) | (pb_edge & pb_previous_state);

	// Update falling/rising edge
	pb_falling_edge = pb_edge & pb_previous_state;
	pb_rising_edge = pb_edge & pb_debounced_state;

	TCB0.INTFLAGS = TCB_CAPT_bm;
}
```

# Serial Communication
# UART
#### Example Configuration & Usage
```c
void uart_init(void){
	PORTB.DIRSET = PIN2_bm; // Enable PB2 as output (USART0 TXD)
	USART0.BAUD = 1389; // 9600 baud @ 3.3Mhz
	USART0.CTRLB = USART_RXEN_bm | USART_TXEN_bm; // Enable TX/RX
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
<div style="page-break-after: always;"></div>

#### Interrupt Handling
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

#### Time Multiplexing Example
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



# SPI
#### Configuration & Usage Example
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
#### Studio Example:
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
volatile uint8_t digit1;
volatile uint8_t digit2; 
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
<div style="page-break-after: always;"></div>

# Pulse Width Modulation
#### TCA0 Initialisation  
```c
void pwm_init() {
	// TCA0 will conrol LED DISP DP (PB5), so we need to enable it as an output
	PORTB.OUTSET = PIN5_bm; // LED off initially
	PORTB.DIRSET = PIN5_bm; // Enable PB5 as output

	// We also need to change the PORTMUX settings so TCA0WO2 is on PB5 (default is PB2)
	PORTMUX.TCAROUTEA = PORTMUX_TCA02_ALT1_gc;

	// CLK_PER select, /2 prescaler (1.67MHz)
	TCA0.SINGLE.CTRLA = TCA_SINGLE_CLKSEL_DIV2_gc;
	// Single-slope PWM mode, WO2 enable (PB5, LED DISP DP)
	TCA0.SINGLE.CTRLB = TCA_SINGLE_WGMODE_SINGLESLOPE_gc | TCA_SINGLE_CMP2EN_bm;
	// Enable overflow interrupt (interrupt at TOP)
	TCA0.SINGLE.INTCTRL = TCA_SINGLE_OVF_bm;
	// Set PWM frequency to 50Hz
	TCA0.SINGLE.PER = 33333; // 50Hz is 33333 clocks @ 1.67 MHz
	// Set duty cycle to 100% initially (LED is active low, so this is OFF)
	TCA0.SINGLE.CMP2 = 33334; // Greater than PER => 100% duty cycle
	// Enable TCA0 (note |= so we dont clobber clock selection)
	TCA0.SINGLE.CTRLA |= TCA_SINGLE_ENABLE_bm;
}
```
#### Changing the Duty-Cycle
```c
int main(void){
	cli(); // Disable interrupts
	pwm_init(); // Initialise timer TCA0
	_delay_ms(1000); // wait 1 second
	TCA0.SINGLE.CMP2BUF = 25000; // 75% duty
	_delay_ms(1000); // wait 1 second
	TCA0.SINGLE.CMP2BUF = 16667; // 50% duty
	_delay_ms(1000); // wait 1 second
	TCA0.SINGLE.CMP2BUF = 8333; // 25% duty
	_delay_ms(1000); // wait 1 second
	TCA0.SINGLE.CMP2BUF = 0; // 0% duty
	_delay_ms(1000); // wait 1 second

	sei(); // Enable interrupts

	// This program is interrupt driven
	// main() will just idle here
	while(1);
}
ISR(TCA0_OVF_vect){
	// This variable is declared static 
	// its value will persist between invocations of the ISR
	static uint16_t compare;
	// Implement an asymmetric soft flash (~1Hz)
	compare += 1310;
	TCA0.SINGLE.CMP2BUF = compare; // update duty cycle
	TCA0.SINGLE.INTFLAGS = TCA_SINGLE_0VF_bm; // acknowledge interrupt
}
```

# Analogue to Digital Conversion
#### ADC Potentiometer Example
```c
void adc_init(){
	// Enable ADC
	ADC0.CTRLA = ADC_ENABLE_bm;
	// /2 clock prescaler
	ADC0.CTRLB = ADC_PRESC_DIV2_gc;
	// Need 4 CLK_PER cycles @ 3.3MHz for 1us, select VDD as ref
	ADC0.CTRLC = (4 << ADC_TIMEBASE_gp) | ADC_REFSEL_VDD_gc;
	// Sample duration of 64
	ADC0.CTRLE = 64;
	// Free running, left adjust result
	ADC0.CTRLF = ADC_FREERUN_bm | ADC_LEFTADJ_bm;
	// Select AIN2 (potentiometer R1)
	ADC0.MUXPOS = ADC_MUXPOS_AIN2_gc;
	// Select 12-bit resolution, single-ended
	ADC0.COMMAND = ADC_MODE_SINGLE_12BIT_gc | ADC_START_IMMEDIATE_gc;
}
```
#### ADC Use
```c
int main(void){
	uint16_t result;
	adc_init();
	serial_init();

	while(1){
		// 12-bit result in bits 15..4
		result = ADC0.RESULT;

		// Print the most significant 8 bits
		printf("%02X\n", result >> 8);
		// Wait 1 second
		_delay_ms(1000);
	}
}
```

# State Machines
#### Implementation Example
```c
typedef enum 
{
	INIT,
	THREE,
	TWO,
	ONE,
	GO
} state_type;

int main(void){
	state_type state = INIT;
	while (1){
		switch (state){
			case INIT:
				if (pb_rising & PIN4_bm){ // S1 released
					state = THREE; // Next state is THREE
					printf("3...");
					pattern1 = segs[0];
					pattern2 = segs[3];
				}
				break;
			case THREE:
				if (pb_rising & PIN4_bm){ // S1 released
					state = TWO; // Next state is TWO
					printf("2...");
					pattern1 = segs[0];
					pattern2 = segs[2];
				}
				break;
			case TWO:
				if (pb_rising & PIN4_bm){ // S1 released
					state = ONE; // Next state is ONE
					printf("1...");
					pattern1 = segs[0];
					pattern2 = segs[1];
				}
				break;
			case ONE:
				if (pb_rising & PIN4_bm){ // S1 released
					state = GO; // Next state is GO
					printf("GO!\n");
					pattern1 = segs[0];
					pattern2 = segs[0];
				}
				break;
			case GO:
				if (pb_rising & PIN7_bm){ // S1 released
					state = INIT; // Next state is INIT
					pattern1 = pattern2 = INIT_PATTERN;
					
				}
				break;
			default:
				state = INIT;
			
		}
	}
}
```

# Serial Protocols 
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