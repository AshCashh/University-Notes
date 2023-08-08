#cs
# Microcontroller
A microcontroller is a small computer on a single [[Integrated Circuits|Integrated Circuit]] chip. A microcontroller contains one or more CPUs along with memory and programmable input/output peripherals. Program memory in the form on RAM, flash or ROM is also often included on the chip. Microcontrollers are designed for embedded applications, in contrast to the microprocessors used in personal computers or other general purpose applications consisting of various discrete chips.

# Microprocessor
A microprocessor is a computer processor where the data processing logic and control is included on a single [[Integrated Circuits|Integrated Circuit]] or a small number of ICs. The microprocessor contains the arithmetic, logic and control circuitry required to perform the functions of a computer's CPU. The IC is capable of interpreting and executing program instructions and performing arithmetic operations. The microprocessor is a multipurpose, clock-driven, [[Resistor]]-based, digital IC that accepts [[Binary]] data as input, processes it according to [[Instructions]] stored in its memory, provides results as output. Microprocessors contain both combinational logic and sequential digital logic and operate on numbers and symbols represented in the binary number system.

While a microcontroller puts the CPU and all peripherals onto the same chip, a microprocessor houses a more powerful CPU on a single chip that connects to external peripherals. The peripherals include memory, [[Input & Output|I/O]], and control units. The QUTy uses a microcontroller called ATtiny1626, that are within a family of microcontrollers called AVRs.

## ATtiny1626 Microcontroller
The ATtiny1626 microcontroller has the following features: 
• CPU: AVR Core (AVRxt variant) 
• Memory: 
	– Flash memory (16KB) used to store program instructions in memory – SRAM (2KB) used to store data in memory 
	– EEPROM (256B) 
• Peripherals: Implemented in hardware (part of the chip) in order to offload complexity

## Flash Memory
• Non-volatile - memory is not lost when power is removed 
• Inexpensive 
• Slower than SRAM 
• Can only erase in large chunks 
• Typically used to store program data 
• Generally read-only. Programmed via an external tool, which is loaded once and remains static during the lifetime of the program 
• Writing is slow

## SRAM 
• Volatile — memory is lost when power is removed 
• Expensive 
• Faster than flash memory and is used to store variables and temporary data 
• Can access individual bytes (large chunk erases are not required)

## EEPROM 
• Older technology 
• Expensive 
• Non-volatile 
• Can erase individual bytes

## Status Register (SREG)
The status register is a 8-bit register that stores the result of the last operation performed by the ALU. It has the following flags: 
**C** Carry Flag 
**Z** Zero Flag 
**N** Negative Flag 
**V** [[Two's Complement]] Overflow Flag 
**S** Sign Flag 
**H** Half Carry Flag 
**T** Transfer Bit 
**I** Global Interrupt Enable Bit

## Microcontroller Pins
Microcontrollers are interfaced via their exposed pins. These pins are the only means to access inputs and outputs, and they are used to interface with other electronic [[Circuit|Circuits]] in order to achieve a required functionality. Pins can be used for:
- General purpose input and output (GPIO) - pin represents a digital state
- Peripheral functions
- Other functions (power supply, reset input, clock input, etc)

Pins are typically organised into groups of related IO banks, reffered to as ports on the AVR microcontroller. These ports and pins are assigned an alphanumeric identifer, (e.g. PB& for pin 7 on port B)
![Pasted image 20230313222825.png](app://local/Users/ashasaunders/Downloads/ash's%20vault/Pasted%20image%2020230313222825.png?1678710505327)
To summarise this diagram:
- The data direction register (DIR) controls the push-pull output enable
- The output driver register (OUT) drives the output state
- The input register (IN) reads the output state
- The [[Pull-up & Pull-down Resistors|internal pull up resistor]] is enabled through software
- The physical voltage on the pin can be routed to an analogue to digital converted (ADC)
- Other peripheral functions can override port pin configurations and the output state

## Multiplexing on the ATtiny1626
On the ATtiny 1626 microcontroller, peripheral functions automatically override standard PORT functions when a coresponding peripheral function is enabled
- Example: Enabling TWI0 via the TWI0.MCTRLA register will cause the peripheral to take control of PB0..1 pin functions
For peripherals that can have input/outputs mapped to different sets of pins, the Port Multiplexer (PORTMUX) can be used to select which pin set should be used by a peripheral 
- Note that not all peripherals have alternative pin locations