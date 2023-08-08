
---
alias: Assembly
---
#cs
## Flow control
Instructions on the AVR Core increment the PC by 1 or 2 (depending on whether the OPCODE is 1 or 2 words) when they are executed so that any successive [[Instructions]] are executed after the first. To divert execution to a different location, we can utilise change of flow instructions.
The jmp (jump) instruction is used to simply jump to a different location in the program. This instruction is capable of jumping to an address within the entire 4M (words) program memory, however, this is highly excessive for the ATtiny1626.

## Labels
Most change of flow instructions take an address in program memory as a parameter. Hence to make this process easier, we can use labels to refer to locations in program memory (and also RAM).
```
jmp new_location ; Jump to the label 
ldi r16, 1 ; skipped

new_location: ; Label
	push r16
```
When a label appears in source code, the assembler replaces references to it with the address of the directive/instruction immediately following that label. Labels work for both absolute and relative addresses and the assembler will automatically adjust the address to the correct type. Additionally, labels can also be used as parameters to other immediate instructions if we store the high and low bytes in registers and wish to reference the location in the indirect jumping instruction.

## Absolute and Relative Addresses
jmp is a 32-[[Binary|bit]] [[Instructions|Instruction]], which uses 22 bits to specify an address between 0x00000000 and 0x3FFFFF, or $2^{23}-1$ bits of memory (8MB). As mentioned early, this is much larger than what the 16-bit PC can address on the ATtiny1626 (64KB).

As we will only need to jump within 64KB of memory, it is inefficient to use the jmp instruction as it requires 3 CPU cycles to execute. Therefore, many AVR change of flow instructions take a value that is added onto the current PC to calculate the destination address, allowing them to fit within 16 bits. The rjmp (relative jump) instruction is therefore more suitable as it only requires 2 CPU cycles.
Note the assembler will throw an error if the address is not within the range of the PC.

## Branching
A branching [[Instructions|Instruction]] jumps to a different location based on a condition, i.e. user input, internal state, or other external factors. Many change of flow instructions are conditioned, and will alter the PC differently based on [[Register]] value(s) or flags. In AVR there are two main categories of branching instructions:
- Branch instructions
- Skip instructions

### Branch Instructions
Branch instructions use the following logic:
1. Check if the specified flag in [[Microprocessors & Microcontrollers#Status Register (SREG)|SREG]] is cleared/set
2. If true, jump to the specified address (PC $\leftarrow$ PC + k + 1)
3. Otherwise, proceed to the next instruction as normal (PC $\leftarrow$ PC + 1)

Althought there are 20 branch instructions listed in the instruction set summary, the following two form the basis of all branching instructions:
- brbc (branch if bit in SREG is cleared)
- brbs (branch if bit in SREG is set)

All other branching instructions are specific cases of the above instructions, that are provided to make programming in Assembly easier. As these instructions check the bits in the SREG, they are usually preceded by an ALU operation such as cp or cpi to trigger the required flags. 
As only 7 bits are allocated to the destination in the OPCODE, branch instructions jump shorter distances than relative jumps.

### Compare Instructions
Both the `cp` and `cpi` instructions are used to compare the values in one or two registers. The ALU performs a subtraction operation whose result is used to update the SREG. Note that the result is not stored or used in any way.
- cp Rd, $Rr$ performs Rd - $Rr$
- cpi Rd, K performs Rd - K
```
ldi r16, 0
ldi r19, 10
cp r16, r19 ; Compare values in registers r16 and r19
brge new location ; Branch if r16 greater than or equal to r19

new_location:
```
Note that many instructions are able to set the Z flag, which is used to indicate if the result of the operation is zero. In these vases, the compare instruction may be redundant.

### Skip Instructions
The skip instructions are less flexible than branch instructions, but can sometimes require less space or fewer cycles. Skip instructions skip the next instruction if the condition is true.
In this example we will skip the line which increments r16.
```
cpse r16, r17 ; Skips next instruction if r16 == r17
inc r16 ; This is skipped
```
Same example which uses a branch instruction:
```
cp r16, r17
breq new_location ; Skips to new_location if r16 == r17
inc r16 ; This is skipped

new_location ; PC is now here
```
Note that the number of cycles for a skip instruction depends on the size of the instruction being skipped. The sbrc and sbrs instructions are used to skip the next instruction if the specified bit a register is cleared/set
```
ldi r16, 0b00101110

sbrc r16, 0 ; Skips next instruction if bit 0 of r16 is cleared
inc r16 ; This is skipped
```
Comparing with branch instructions
```
ldi r16, 0b00101110
andi r16, 0b00000001 ; Isolate bit 0
breq new_location ; Skips next instruction if r16 == 0
inc r16 ; This is skipped

new_location: ; Pc is now here
```
The sbis and sbic instructions are used to skip the next instruction if the specified bit an I/O register is set/cleared. For example, if we wish to toggle the decimal point LED (DISP DP) on the QUTy (PORT B pin 5) when the first button (BUTTON0) was pressed (PORT A pin 4),
```
ldi r16, PIN5_bm ; Bitmask of pin 5
sbis VPORTA_IN, 0b00010000 ; Skip next instruction if pin 4 of PORT a is set
sts PORTB_OUTTGL, r16 ; Toggle the output driver of pin 5 on PORT B
```
Using branch instructions:
```
in r17, VPORTA_IN ; Read the input register of PORT A
andi r17, 0b00010000 ; Isloate pin 4

brne new_location ; Skips instructions if r17 != 0

ldi r16, PIN5_bm ; Bitmask of pin 5
sts PORTB_OUTTGL, r16 ; Toggle the output driver of pin 5 on PORT B

new_location:
```
## Loops
By jumping to an earlier address, you can run instructions multiple times:
```
infinite_loop:
	; Code to repeat
	jrmp infinite_loop
```
Loops can also be finite, in which case the loop will terminate when a counter reaches 0.
```
ldi r16, 10 ; Set counter to 10
loop:
	dec r16 ; Decrement counter
	brne loop ; Branch if counter != 0
```
Loops can also be used to repeat until some external event occurs (e.g. a button is pressed)
```
main_loop:
	in r17, VPORTA_IN ; Read the input reader of PORT A
	andi r17, 0b00010000 ; Isolate pin 4

	brne main_loop ; Branch if counter !=0
	rjmp button_pressed

button_pressed: 
	; Execute instructions
	rjmp main_loop ; Return to main loop
```
### Delay Loops
Loops can be utilised to delay the execution of instructions. These instructions do not execute any useful code. This is useful for when we wish to wait for an external event to occur. 
To create a precisely timed delay, we must take the following values into account.
- The clock speed - frequency of the clocks oscillations (default 20MHz or 32.768kHz - configurable in CLKCTRL_MCLKCTRLA)
- The prescaler - reduces the frequency of the CPU clock through division by a specific amount; 
   12 differeent settings from 1x to 64x (default: 6 - configurable in CLKCTRL_MCLKCTRLA)
The clock oscillates at its effective clock speed:
$$ Effective\space Clock\space Speed = clock\space speed \times \cfrac{1}{prescaler} $$
The default prescaler is 6, so the effective clock speed is 3.33MHz by default. Note that the effective clock speed can therefore range between:
- Effective maximum clock frequency: 20MHz (20MHz clock & prescaler 1)
- Effective minimum clock frequency: 512Hz (32.768 kHz clock & prescaler 64)

Therefore to create a delay, we must first determine the required number of CPU cycles in the body of the loop and iterate until the number of CPU cycles reaches the required amount.

The following examples utilise counters of various sizes to create delays. Note that $n$ represents the number of iterations.
```
delay_1:
ldi r16, x ; 1 CPU cycle
ldi r17, 1 ; 1 CPU cycle ; Incrementor

loop:
	add r16, r17 ; 1 CPU cycle
	brcc loop ; 2 CPU cycles (1 CPU cycle when condition is false)
```
The register r16 has the following relationship:
$$x=(2^8-1)-n\Leftrightarrow n = (2^8-1)-x$$
with,
$$total\space cycles = 1+1+(n+1)+2n+1 = 3n+4$$
for a maximum delay of 230.7$\mu$s $((3\times(2^8-1)+4)T)$, where T is the period of one CPU cycle: $T=\cfrac{1}{20MHz/6}=300ns$

To create larger delays, we can use multiple registers:
```
delay_2:
	ldi r24, x ; 1 CPU cycle
	ldi r25, y ; 1 CPU cycle

	loop:
		adiw r24, 1 ; 2 CPU cycles
		brcc loop ; 2 CPU cycles (1 when condition is false)
```
The register pair $(y:x)$ has the following relationship:
$$(y:x)=(2^{16}-1)-n\Leftrightarrow n = (2^{16}-1)-(y:x)$$
with, 
$$ total\space cycles = 1+1+2(n+1)+2n+1 = 4n+5$$
for a maxiumum delay of 78.644ms $((4\times(2^{16})+5)+T)$.

With three registers,
```
delay_3:
	ldi r24, x ; 1 CPU cycle
	ldi r25, y ; 1 CPU cycle
	ldi r26, z ; 1 CPU cycle

	loop:
		adiw r25, 1 ; 2 CPU cycles
		adc r26, r0 ; 1 CPU cycle (r0 = register w/ value 0)
		brcc loop ; 2 CPU cycles (1 CPU cycle with condition is false)
```
The register triplet $(z:y:x)$ is determined through:
$$(z:y:x)=(2^{24}-1)-n\Leftrightarrow n = (2^{24}-1)-(z:y:x)$$
with, 
$$ total \space cycles = 1+1+1+2(n+1)+(n+1)+2n+1 = 5n+7$$
for a maximum delay of 25.166s $((5\times(2^{24}-1)+7)T)$. This approach can be extended to create delays of any length

If needed, we can also include the nop (no operation) instruction which requires 1 CPU cycle and does nothing. In addition to this, we can also utilise nested loops, however the timing is more complex to determine.

## Memory and IO
On the AVR Core, as both I/O and SRAM are accessed through the data space, they can be directly accessed using instructions that read/write to memory. This approach is known as memory-mapped I/O (MMIO) and it significantly reduces chip complexity.

In contrast to modern CPU architectures, such as x86, in the AVR architecture, programs are located in a separate address space (although the memory is still accessible through the data space).
![Pasted image 20230320143751.png](app://local/Users/ashasaunders/Downloads/ash's%20vault/Pasted%20image%2020230320143751.png?1679287071625)
The following instructions may be used to access memory from the data space:
- lds (load direct from data space to register)
- sts (store direct from register to data space)
- ld (load indirect from data space to register)
- st (store indirect from register to data space)
- push/pop (stack operations in SRAM - starting at 0x3800 or 3KB)
- in/out (single cycle I/O register operations)
- sbi/cbi (set/clear bit in I/O register)

Note that the in/out instructions can only access the low 64 bytes of the I/O register space and the sbi/cbi instructions can only access the low 32 bytes of the I/O register space.
As the name suggests, these instructions only require a single CPU cycle and hence several addresses such as VPORT{A, B, C} (virtual ports) are mapped to this location, for fast access.

## Load/Store Indirect
While the lds/sts instructions can be used to access addresses of bytes, they are generally not suitable for accessing data structures such as arrays. Instead, we can use the ld/st instructions to take advantage of their 16-bit pointer registers, which support some pointer arithmetic. ld/st allow transfers between a register and data space, where the address is stored in a pointer register.

The pointer registers avaliable for use by ld/st are X, Y, Z, which occupy the same space as r16...r31. Can refer to these as:
- r26 → XL (X-register low byte)
- r27 → XH (X-register high byte) 
- r28 → YL (Y-register low byte) 
- r29 → YH (Y-register high byte) 
- r30 → ZL (Z-register low byte) 
- r31 → ZH (Z-register high byte)
For example, if we wanted to access a byte in RAM, we can do the following:
```
; Store address of RAM in X
ldi XL, lo8(RAMSTART) ; Low byte of X (aka r26)
ldi XH, hi8(RAMSTART) ; High byte of X (aka r27)

ld r16, X ; Load byte from X to r16
; The byte in X is now in r16

ldi r17, 24
st X, r17 ; Store byte from r16 to X
; The byte in X (and hence at RAMSTART) is now 24
```
These pointer registers also support post-increment and pre-decrement operations:

X+ (post-increment pointer address)
```
ld r16, X+ ; Load byte from X to r16, then X <- X + 1
st X+, r16 ; Store byte from r16 to X, then X <- X + 1
```
```
; Copy 100 bytes from X to Y
ldi r16, 100
loop: 
	ld r0, X+ ; Loads into r0, then X <- X + 1
	st Y+, r0 ; Stores from r0, then Y <- Y + 1
	dec r16
	brne loop
```
-X (pre-decrement pointer address)
```
ld r16, -X ; X <- X - 1, then load byte from X to r16
st -X, r16 ; X <- X - 1, then store byte from r16 to X
```
This operation can be used to copy bytes from one location to another
```
; Copy 10 bytes from RAM to RAM+10
ldi XL, lo8(RAMSTART)
ldi XH, hi8(RAMSTART)

ldi YL, lo8(RAMSTART+10)
ldi YH, hi8(RAMSTART+10)

ldi r16, 10 ; Loop 10 times
loop: 
	ld r0, X+ ; Load byte from X to r0, then X <- X + 1
	st Y+, r0 ; Store byte from r0 to Y, then Y <- Y + 1
	dec r16
	brne loop
```
## Load/Store Indirect with Displacement
In addition to the ls/st instructions , the ldd/std instructions are a special form that allow us to load/store from/to the address to the pointer register **plus** q = {0 to 63}.
```
ldi YL, lo8(RAMSTART)
ldi YH, hi8(RAMSTART)

ldd r0, Y+20 ; Load byte from Y+20 to r0
std Y+21, r0 ; Store byte from r1 to Y+21
; Note Y still points to RAMSTART
```
Note this form is only avaliable for Y, and Z

## Stack
The stack is a last-in first-out (LIFO) data structure in SRAM. It is accessed through a register called the stack point (SP), which is not part of the register file like SREG. 
Upon reset, SP is set to the last avaliable address in SRAM (0x3FFF), and can be modified through push/pop and other methods that are generally not reccomended.
- push stores a register to SP's location then decrements SP (SP <-- SP - 1)
- pop increments SP (SP <-- SP + 1) then loads a register from SP's location

If a particular register is required without modifying other code, we can temporarily store the value of that register on the stack, and pop it back when we  are done:
```
push ZL ; Temporarily store Z on the stack
push ZH 
; Z may be used for another purpose
pop ZH ; Restore Z from the stack in reverse order
pop ZL 
```

## Procedures
Procedures allow us to write modular, reusable code which makes them powerful when working on complex projects. Although they are usually associated with high level languages as methods or functions, they are also avaliable in assembly.
Procedures begin with a label and end with the ret keyword. They must be called using the call / recall instructions.
```
procedure:
	; Procedure body
	ret ; Return to caller
```
### Saving Context
To ensure that procedures are maximally flexible and place no constraints on the caller, we must always restore any modified registers before returning to the caller. The same is true for the SREG.
```
rjmp main_loop

procedure:
	push r16 ; Save r16 on the stack
	; Code that possibly modifies r16
	pop r16 ; Restore r16 from the stack
	ret

main_loop:
	ldi r16, 10
	rcall procedure ; Call procedure
	push r16 ; r16 should still be 10
```
Example: (assumes buttons are already initilised)
```
WaitForButton:
push r0 ; Saves r0
in r0, CPU_SREG
push r0 ; Saves CPU.SREG

WaitForButton_loop:
in r0, VPORTA_IN
ori r0, 0b00001111
com r0 ; One's complement
breq WaitForButton_loop
pop r0
out CPU_SREG, r0 ; Restore CPU.SREG
pop r0 ; Restore r0
ret
```
### Parameters and Return Values
Useful procedures often want to take parameters and/or return values. There are several ways to do this in AVR:
- Using registers. This is usually the preffered approach as we have a lot of registers and they are efficient to manipulate
- Using the stack. This may be necessary if the data being passed is too big for register space
For return values the best approach is usually to just store the value in a register.
```
rjmp main_loop

; Calculate the average of two numbers
; Inputs:
;    r16: first number
;    r17: second number
; Outputs:
;    r16: average

average: 
	push r0 ; Save r0
	in r0, CPU_SREG ; Save SREG
	push r0

	; Calculate average
	add r16, r17
	ror r16

	pop r0 ; Restore SREG
	out CPU_SREG, r0
	pop r0 ; Restore r0
	ret

main_loop:
	; Arguments
	ldi r16, 100
	ldi r17, 200
	rcall average ; Now r16 contains 150

```
Using the stack:
```
; Calculate the average of two numbers
; Inputs:
;     top two values on stack
; Outputs:
;     r16: average

average:
	push ZL ; Save Z
	push ZH
	in ZL, CPU_SREG ; Save SREG
	push ZL
	push r17 ; Save r17
	in ZL, CPU_SPL ; Get SP location
	in ZH, CPU_SPH 

; Get numbers number
ldd r16, Z+7
ldd r17, Z+6

; Calculate Average
add r16, r17
ror r16

pop r17 ; Restore r17
pop ZL ; Restore SREG
out CPU_SREG, ZL
pop ZH ; Restore Z
pop ZL
ret

main_loop:
	; Arguments
	ldi r16, 100
	push r16
	ldi r16, 200
	push r16
	recall average

	; Remove arugments from the stack
	pop r0 ; Must discard
	pop r0 ; Old paramaters 
```

## Configuring an Output in Assembly
1. Place the port pin in a safe initial state by writing to the OUT (or OUTSET/OUTCLR) [[Register]] (HIGH or LOW depending on the context)
2. Configure the port pin as an output by setting the corresponding bits in the DIR [[Register]]
3. Set the desired pin state by writing to the OUT register
```c
; Load macros for easy access to port data space addresses
#include <avr/io.h>

; Bitmask for pin 5 (0b00100000)
ldi r16, PIN5_bm

; Set initial safe state
sts PORTB_OUTCLR, r16 ; LOW if active HIGH
sts PORTB_OUTSET, r16 ; HIGH if active LOW

; Enable output
sts PORTB_DIRSET, r16 ; Enable output on PB5

; Set output state to desired value
sts PORTB_OUTSET, r16 ; Set state of PB5 to HIGH
```
### Configuring an Input in Assembly
1. If required, enable the internal [[Pull-up & Pull-down Resistors|pull-up resistor]] by setting the PULLUPEN bit in the coresponding PINnCTRL register
2. Read the IN register to get the current state of the pin (You may like to use a bit mask to isolate the bit for the relevant pin)
3. Isolate the relevant pin using the [[Logical Operators#Conjunction (AND)|AND]] operator
```
ldi r16, PIN5_bm (0x08)

; Enable internal pull-up resistor if required
sts PORTB_PIN5CTRL, r16

; Read output state from data space
lds r17, PORTA_IN
; Read output state using virtual PORT
in r17, VPORTA_IN

; Isolate desired pin
andi r17, r16
```
Note: ON reset the DIR register is cleared so pins are configured as input-only by default.
