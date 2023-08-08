#cs
An interrupt is a signal sent to the processor to indicate that it should interrupt the current code that is being executed to execute a function called an **interrupt service routine** (or interrupt handler). Rather than polling for individual events (such as button presses), interrupts allow the processor to be notified when an event occurs.

Summarised Interrupts are used by hardware/peripherals to let the CPU know something has happened. They are commonly used in [[Microprocessors & Microcontrollers]].

## Common Functions of Interrupts 
[[Operating Systems]] are interrupt driven. Interrupt transfers control to the ISR through the interrupt vector, which contains the addresses of all the service routines. Interrupt architecture must save the address of the interrupted [[Instructions|Instruction]]. 

A trap or exception is a software-generated interrupt caused either by an error or a user request. 

## Interrupt Handling 
The operating system preserves the state of the CPU by storing register and the program counter. It then determines which type of interrupt occurred, polled or vectored interrupt system.

Once determined what caused the interrupt, separate segments of code determine what action should be taken for each type of interrupt.


## Interrupts and the AVR
On the ATtiny1626, interrupts work as follows:
1. An interupt-worthy event occurs. (e.g. data transferred, overflow of a timer)
2. The appropriate interrupt flag (INTFLAGS) in he peripheral is set.
3. If the corresponding interrupt is enabled (INTCTRL field of the peripheral), the interrupt is triggered and we proceed to the following step.
4. If the global interrupt flag (SREG.I) is set, the interrupt can be executed and we proceed to the following step.
5. The PC is pushed onto the stack and jumps to the interrupt vector (the address of the interrupt handler) See page 63-64 on datasheet.

### Interrupt Vectors
The interrupt vector is a table of addresses that the processor jumps to when an interrupt is triggered. These addresses are usually at the beginning of the program memory.

### Interrupt Service Routine
The code that handles the interrupt is called the interrupt service routine (ISR) (or interrupt handler). The ISR is a function that is executed as a result of the interrupt.
When configuring an interrupt, we must temporarily disable interrupts globally to prevent the interrupt from being triggered while we are configuring it.
```c
cli(); // Disable interrupts globally
// Configure interrupts
sei(): // Enable interrupts globally
```
It is also important to restore the state of the CPU or registers before the ISR returns. This is because another interrupt can be triggered while the ISR is executing. To tackle this, we can use the `ISR` macro from the `avr/interrupt.h` header file which will automatically save and restore the state of the CPU and registers.
```c
#include <avr/interrupt.h>

ISR(TCBO_INT_vect) {
	// Interrupt service routine for TCBO
}
```
The header file also sets aside program memory for the interrupt vector table.

### Interrupt Flags
Each peripheral has an interrupt flag field (INTFLAGS) that is set when the conditions for that interrupt occur (even if interrupts are disabled). The exact format of this field depends on the type of interrupt, but in general a bit is set for the type of interrupt.

As some peripherals have 1 interrupt vector with multiple interrupt sources, the interrupt flag fields can be used to determine the exact source of the interrupt.
The interrupt flag field is cleared by writing a 1 to the corresponding bit.

### Peripheral Interrupts
Peripherals differ in what causes interrupts to be raised and many have multiple interrupt sources.

**Port Interrupts**
To configure `BUTTON0` as an interrupt source, we must enable the interrupt in the `PORTA.PIN4CTRL` peripheral.
```c
ISR(PORTA_PORT_vect) {
	// Interrupt service routine for PORTA
	VPORTA.INFLAGS = PIN4_bm; // Clear interrupt flag
}
cli();
// Enable pull-up resistor and interrupt on falling edge
PORTA.PIN4CTRL |= PORT_BULLUPEN_bm | PORT_ISC_FALLING_gc;
sei();
```
### Interrupts and Synchronisation
ISR's may interact with state used by other code running at the same time, which can cause problems with synchronisation, similar to those faced with multithreaded programming. To avoid this, we should make use of the `volatile` keyword so that the compiler does not make assumptions about variable states. The `cli` and `sei` functions can also be used to disable interrupts and create a memory barrier which prevents instructions from being reordered by the compiler.