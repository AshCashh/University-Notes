#cs
A register refers to a memory location that is 1 byte in size (8-bit). The ATtiny1626 has 32 registers of which r16 to r31 can be loaded with an immediate value (0 to 255) using ldi.
```c
ldi r16, 17 ; Load the value 17 into r16
```
Values are commonly loaded into registers as many other operations can be performed on them.