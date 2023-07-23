#cs
[[Instructions]] on the AVR Core increment the PC by 1 or 2 (depending on whether the OPCODE is 1 or 2 words) when they are executed so that any successive instructions are executed after the first. To divert execution to a different location, we can utilise change of flow instructions.
The jmp (jump) instruction is used to simply jump to a different location in the program. This instruction is capable of jumping to an address within the entire 4M (words) program memory, however, this is highly execessive for the [[Microprocessors & Microcontrollers#ATtiny1626 Microcontroller|ATtiny1626]].

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
jmp is a 32-bit instruction, which uses 22 bits to specify an address between 0x00000000 and 0x3FFFFF, or $2^{23}-1$ bits of memory (8MB). As mentioned early, this is much larger than what the 16-bit PC can address on the ATtiny1626 (64KB).

As we will only need to jump within 64KB of memory, it is inefficient to use the jmp instruction as it requires 3 CPU cycles to execute. Therefore, many AVR change of flow instructions take a value that is added onto the current PC to calculate the destination address, allowing them to fit within 16 bits. The rjmp (relative jump) instruction is therefore more suitable as it only requires 2 CPU cycles.
Note the assembler will throw an error if the address is not within the range of the PC.