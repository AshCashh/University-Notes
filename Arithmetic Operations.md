#cs
Addition is performed using the same process as decimal addition except we only use two digits, 0 and 1.
- 0b0 + 0b0 = 0b0
- 0b0 + 0b1 = 0b1
- 0b1 + 0b1 = 0b10
When adding two 1's, we carry the result into the next [[Binary|bit]] position as we would with a 10 in decimal addition. in AVR [[Assembly Programming|Assembly]], we can use the add [[Instructions|instruction]] to add two bytes. The following example adds two bytes.
```
; Accumulator
ldi r16, 0

; First number
ldi r17, 29
add r16, 17 ; R16 <- R16 + R17 = 0 + 29 = 29

; Second number
ldi r17, 118
add r16, 17 ; R16 <- R16 + R17 = 29 + 118 = 147
```
## Overflows
When the sum of two 8-bit numbers is greater than 8-bit (225), an overflow occurs. Here we must utilise a second [[Register]] to store the high byte so that the result is represented as a 16-bit number. To avoid loss of information, a carry bit is used to indicate when an overflow has occurred. This carry bit can be added to the high byte in the event that an overflow occurs. The following example shows how to use the adc instruction to carry the carry bit when an overflow occurs.
```
; Low byte 
ldi r30, 0
; High byte
ldi r31, 0

; Empty byte for adding carry bit
ldi r29, 0

; First number 
ldi r16, 0b11111111
; Add to low byte
add r30, r16 ; R30 <- R30 + R16 = 0 + 255 = 255, C <- 0
; Add to high byte
adc r31, r29 ; R31 <- R31 + R29 + C = 0 + 0 + 0 = 0

; Second number
ldi r16, 0b00000001
; Add to low byte
add r30, r16 ; R30 <- R30 + R16 = 255 + 1 = 0, C <- 1
; Add to high byte
adc r31, r29 ; R31 <- R31 + R29 + C = 0 + 0 + 1 = 1
```
Therefore the final result is R31:R30 = 0b00000001:0b00000001 = 256.

## Subtraction
Subtraction is performed using the same process as binary addition, with the subtrahend in [[Two's Complement]] form. In the case of overflows, the carry bit is discarded

## Multiplication
Multiplication is understood as the sum of a set of partial products, similar to the process used in decimal multiplication. Here each digit of the multiplier is multiplied to the muliplicand and each partial product is added to the result.

Given an m-bit and an n-bit number, the product is at most (m + n) - bit wide.

Using AVR assembly, we can use the mul instruction to perform multiplication.
```
; First number
ldi r16, 13

; Second number
ldi r17, 43

; Multiply 
mul r16, r17 ; R1:R0 <- 0b00000010:0b00101111 = 2:47
```
The result is stored in the register pair R1:R0

## Division 
Division, square roots and many other functions are very expensive to implement in hardware, and thus are typically not found in conventional ALUs, but rather implemented in software. However, there are other techniques that can be used to implement division in hardware. By representing the divisor in reciprocal form, we can try to represent the number as the sum of powers of 2. 
For example, the divisor 6.4 can be represented as:
$$ \frac{1}{6.3} = \frac{10}{64} = 10 \times 2^{-2} $$
so that dividing an integer n by 6.4 is approximately equivalent to:
$$ \frac{n}{6.4} \approx (n \times 10) \gg 6 $$
When the divisor is not exactly representable as a power of 2 we can use fractional exponents to represent the divisor, however this requires a floating point system implementation which is not provided on the AVR.