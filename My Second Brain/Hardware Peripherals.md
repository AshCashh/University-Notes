#cs
[[Microprocessors & Microcontrollers|Microcontrollers]] typically include a variety of hardware peripherals that remove the burden of having to write software for common functionality such as [[Pulse Width Modulation|PWM]] timers, [[Serial Communication]] and [[Analogue to Digital Conversion]].
They can provide very precise timing and very fast (nanosecond) response times.
Hardware peripherals can run independent of the CPU so that:
- Peripherals can perform tasks without software intervention
- Peripherals are not subject to timing constraints (execution time of [[Instructions]], CPU clock speed)
- The CPU can be used to perform other [[Computation|Computations]] while the peripheral is busy
All control of, and communication with peripherals is done through **peripheral registers** which the CPU can access via the memory map. Peripherals also typically have direct access to [[Hardware]] resources such as pins.

## Configuring Hardware Peripherals
Upon reset, most hardware peripherals are disable by default and must be configured and enabled by writing to the appropriate peripheral [[Register]]. This is often done once at the start of the program, but can be reconfigured dynamically if required, depending on the application. Information about peripheral registers is found in the datasheet and often recommends steps are also provided.
In general:
1. Set bits on peripheral registers to configure the peripheral in the correct mode
2. Enable peripheral interrupts and define an associated ISR, if required
3. Enable the peripheral
It is best practice to globally disable [[Interrupts]] when configuring peripherals

## Timers
Timers provide precise measurements of elapsed clock cycles in hardware, independent of software and the CPU. Timers are used to generate period events (via an interrupt), measure time between two events, generate periodic signals on a pin that are frequency of [[Pulse Width Modulation]] etc.

### Timer Implementations
Most timer implementations are the same basic structure, a counter which is incremented or decremented by a clock/event/etc. By comparing the value of this counter, the timer can perform more complex behaviours such as generating an interrupt, changing pin state, etc.

### Timer Counters
The Attiny1626 has two timers, Timer Counter A and B (TCA/TCB) that are both 16-bit counters. As both timers are highly configurable, the datasheet should be consulted for more information. 

In general, the counter, `CNT`, increments by 1 each clock cycle. The clock cycle can be configured with a prescaler to increase the duration of a timer. 

The capture compare register `CCMP` can be used to generate an interrupt when the counter reaches a certain value.

The period register `PER` can also be used to set the maximum value of the counter. This register can also generate interrupts when the counter reaches the maximum value (overflow).
![[Pasted image 20230501153847.png]]

### Timer Periods
The period $T$ is the duration of a timer cycle, that is the timer before the counter resets to 0. To configure the timer counter to cycle according to this period, we must configure the register `PER`, which is the number of counts $n$ of the timer clock, depending on the clock frequency $f_{clk}$ of the timer clock.
One period of the timer clock is given by:
$$T_{clk} = \cfrac{1}{f_{clk}/prescaler}$$
so that the number of timer clock cycles in a period $T$ is given by:
$$n=\cfrac{T}{T_{clk}}$$
The prescalared used to configure the timer clock leads to a trade-off between the timer period and the timer resolution, as the interval between timer clock cycles $T_{clk}$ is increased.

### Timer Counter B Example Configuration
Configuring the `TCB0` timer in periodic interrupt mode:
To calculate the clock source (Top value) for 3.33MHz:
$$T_{clk}=\cfrac{1}{3.33\times10^6}=300ns$$
$$TOP=\cfrac{T_{timer}}{T_{clk}}=\cfrac{1\times10^{-3}}{300\times10^{-9}}=3333\space counts$$
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

int main(void){
	sei();
	tcb_init();
	cli();
	
	while (1);
}
```
```c
ISR(TCB0_INT_vect){
	// This interrupt will execute every 1ms
	// do something
	TCB0.INTFLAGS = TCB_CAPT_bm;
}
```
### Timer Modes
Timers will typically have a variety of modees that can drastically change how they behave, i.e. how/when the counter is updated, direction of count, capture of counter value into other registers.
![[Pasted image 20230501170000.png]]

## Pushbutton Handling
Pushbuttons have two possible states, pressed and released. Given an active-low pushbutton,
- When the pushbutton is pressed, the pin is pulled low, corresponding to a 0 value
- When the pushbutton is released, the pin is pulled high, corresponding to a 1 value
The state of pushbuttons can be read through a bitwise AND operation with the `PORTA.IN` register
```c
#include <avr/io.h>

PORTA.PIN4CTRL = PORT_PULLUPEN_bm;

while (1){
	if (PORTA.IN & PIN4_bm) {
		// Pushbutton is released
	}
	else {
		// Pushbutton is pressed
	}
}
```
In this loop structure, the state of the pushbutton will be in the pressed state until the pushbutton is released. This may not be desirable if we want to perform a single action when the pushbutton is pressed. To solve this, we must respond to a change in state.
- A falling edge is created when the pushbutton is pressed (transition from 1 to 0)
- A rising edge is created when the pushbutton is released (transition from 0 to 1)
This is known as edge detection. To implement this in C, we can use the XOR operation to detect a change in the signal.
```c
uint8_t pb_prev = 0xFF;
uint8_t pb_state = 0xFF:

while (1){
	pb_prev = pb_state; // Register previous PB state
	pb_state = PORTA.IN; // Sample current PB state
	uint8_t pb_edge = pb_state ^ pb_prev;

	uint8_t pb_falling_edge = pb_edge & pb_prev;
	uint8_t pb_rising_edge = pb_edge & pb_state;

	if (pb_falling_edge & PIN4_bm){
		// Falling edge on PA4 (press event for active-low pushbutton)
		// Code here should only execute once, when the pushbutton is pressed
	}
}
```
To additionally detect a falling/rising edge, we can use the AND operation to detect a change in the signal.

### Pushbutton Sampling
The actuation of mechanical pushbuttons is slow and therefore it is important to sample pushbutton states fast enough to detect changes in state. Latency refers to the delay between user input and the reaction of a system. For user input, latency should be acceptably small; what is acceptably small depends on what magnitude of latency is perceptible and is specififc to the application. Latency as low as 2ms is perceptible in particular user input applications, however latency between 20ms to 60ms is acceptable for most applications.

## Switch Bounce
Switch bounce is an artefact of electromechanical switches where the switch contacts bounce back and forth when the switch is actuated. This results in a signal that is not stable and can cause false positives when detecting a change in state.

As a digital system can sample a voltage much faster than a mechanical switch can change state, the system may detect multiple transitions of the switch state. To prevent this, we can debounce the pushbuttons either by using a debouncing circuit, or software. To implement this in software, we can take multiple samples and only detect a change in state if the samples are consistent over multiple samples. Due to this, it is better to use an ISR to capture the state of the pushbutton at regular intervals.
```c
volatile uint8_t pb_debounced_state = PIN4_bm;
volatile uint8_t pb_falling_edge = 0;
volatile uint8_t pb_rising edge = 0;

// Periodic 1ms interrupt
ISR (TCB0_INT_vect){
	static uint8_t counter = 20;

	// Capture the state of the pushbutton from the port pin
	uint8_t pb_sample = PORTA.IN & PIN4_bm;
	// Detect a change in state
	uint8_t pb_edge = pb_sample ^ pb_debounced_state;

	if (pb_edge){
		counter--;
		if (!counter){
			// Save previous debounced state
			uint8_t pb_previous_state = pb_debounced_state;

			// Update debounced state
			pb_debounced_state = pb_sample;

			// Update falling/rising edge
			pb_falling_edge = pb_edge & pb_previous_state;
			pb_rising_edge = pb_edge & pb_debounced_state;

			// Reset counter
			counter = 20;
		}
	}
	else{
		// Reset counter
		counter = 20;
	}
	TCB0.INTFLAGS = TCB_CAPT_bm;
}
```
The above implementation only debounces a single pushbutton, as the counter only applies to S1. To debounce multiple pushbuttons, it is possibe to use a counter for each pushbutton, however this will lead to a large amount of code, instead we can utilise vertical counter.

### Vertical Counter
Instead of using a counter variable for each pushbutton, we can use the bits of a single variable to represent the counters for each pushbutton. Doing so will reduce the maximum value of the counter, however this will not be a problem as we only require the counter to reach a value of 20.  This following code implements a vericle counter for 4 pushbuttons.
```c
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
This code allows us to debounce up to 8 pushbuttons using a single 8-bit variable. The debounced state of the pushbuttons is stored in `pb_debounced_state`. This variable updates if the state of the pushbutton is consistent over 3 samples, or if a falling edge is detected.

### Studio Example
```c
// Includes everything from last weeks demo


void calc_digits(uint8_t count){
	uint8_t num, tens=0;

	num = count;
	while (num > 9){
		num -= 10;
		tens++;
	}
	pattern1 = segs[tens];
	pattern2 = segs[num];
}

void pb_init(void){

	// PBs PB4-7, enable pullup resistors
	PORTA.PIN4CTRL = PORT_PULLUPEN_bm;
	PORTA.PIN5CTRL = PORT_PULLUPEN_bm;
	PORTA.PIN6CTRL = PORT_PULLUPEN_bm;
	PORTA.PIN7CTRL = PORT_PULLUPEN_bm;

}
voltatile uint8_t pb_debounced = 0xFF;

void pb_debounce(void){
	static uint8_t vcount0=0, vcount1=0; // Vertical counter bits

	uint8_t pb_sample = PORTA.IN;

	uint8_t pb_changed = pb_sample ^ pb_debounced;

	// Vertical counter update
	vcount1 = (vcount1 ^ vcount0) & pb_changed; // vcount1 (bit 1 of vertical count)
	vcount0 = ~vcount0 & pb_changed; // vcount0 (bit 0 of vertical count)
	
	pb_debounced ^= (vcount0 & vcount1); // Toggle pb_debounced
}

// IN TIMER.C
void pb_debounce(void);

// Timer ISR, interrupts every 10ms
ISR(TCB0_INT_vect){
	pb_debounce();
	

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

// MAIN
int main(void){
	serial_init();
	pb_init();
	timer_init();
	spi_init();

	uint8_t pb_sample_r = 0xFF;
	uint8_t pb_sample = 0xFF;
	uint8_t pb_changed, pb_rising, pb_falling;
	uint8_t count = 0;

	while (1){
		pb_sample_r = pb_sample;
		pb_sample = pb_debounced;
		pb_changed = pb_sample ^ pb_sample_r;

		pb_falling = pb_changed & pb_sample_r;
		pb_rising = pb_changed & pb_sample;

		if (pb_sample & PIN4_bm){
			
		}
	}

}
```