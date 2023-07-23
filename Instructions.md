---
alias: Instruction
---
#cs
The CPU understands and can execute a limited set of instructions — ~88 unique instructions for the ATtiny1626 
Instructions are encoded in program memory as opcodes. Most instructions are two bytes long, but some instructions are four bytes long or 32 [[Binary|bits]]
The AVR Instruction Set Manual describes all of the available instructions, and how they are translated into opcodes 

Instructions fall loosely into five categories: 
- Arithmetic and logic — ALU
- Change of flow - jumping to different sections of the code or making decisions 
- Data transfer - moving data in/out of registers, into the data space, or into RAM 
- Bit and bit-test - looking at data in registers (which bits are set or not set) 
- Control - changing what the CPU is doing