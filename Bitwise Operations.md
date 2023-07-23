#cs
When applying [[Logical Operators]] to a sequence of [[Binary|bits]], the operation is performed in a bitwise manner. The result of each operation is stored in the corresponding bit index also.

## Bit Manipulation
Often we need to modify individual bits within a byte, without modifying other bits. This is accomplished by performing a bitwise operation on the byte using a bit mask or bit field. 
- [[#Setting Bits|Set]] specific bits (changed value to 1)
- [[#Clearing Bits|Clear]] specific bits (changed value to 0)
- [[#Toggling Bits|Toggle]] specific bits (change values from 0 -> 1, or 1 -> 0)

### Setting Bits
To **set** a bit, we take the bitwise [[Logical Operators#Disjunction (OR)|Disjunction (OR)]] of the byte, with a bit mask that has a 1 in each position where the bit should be set.
$$ 
\begin{array} {c|lc} 
\large{byte}&\Large1 & \Large1 & \Large0 & \Large0 & \Large1 & \Large0 & \Large0 & \Large0 \\ \hline&&\color{red}\Large\downarrow&&\color{red}\Large\downarrow&&&\color{red}\Large\downarrow&\color{red}\Large\downarrow \\
 \large{bitmask}&\Large0&\Large1&\Large0&\Large1&\Large0&\Large0&\Large1&\Large1 \\
 \hline
 \large{result}&\Large1&\Large1&\Large0&\Large1&\Large1&\Large0&\Large1&\Large1 \\
 \hline
 \end{array}
$$

### Clearing Bits
To **clear** a bit, we take the bitwise [[Logical Operators#Conjunction (AND)|Conjunction (AND)]] of the byte, with a bitmask that has a **0** in each position where the bit should be cleared.
$$ 
\begin{array} {c|lc} 
\large{byte}&\Large1 & \Large0 & \Large1 & \Large1 & \Large0 & \Large0 & \Large1 & \Large1 \\ \hline&&\color{red}\Large\downarrow&&\color{red}\Large\downarrow&&&\color{red}\Large\downarrow&\color{red}\Large\downarrow \\
 \large{bitmask}&\Large1&\Large0&\Large1&\Large0&\Large1&\Large1&\Large0&\Large0 \\
 \hline
 \large{result}&\Large1&\Large0&\Large1&\Large0&\Large0&\Large0&\Large0&\Large0 \\
 \hline
 \end{array}
$$
### Toggling Bits
To toggle a bit, we take the bitwise [[Logical Operators#Exclusive Disjunction (XOR)|Exclusive Disjunction (XOR)]] of the byte, with a bit mask that has a 1 in each position where the bit should be toggled
$$ 
\begin{array} {c|lc} 
\large{byte}&\Large1 & \Large1 & \Large0 & \Large0 & \Large1 & \Large0 & \Large0 & \Large1 \\ \hline&&\color{red}\Large\downarrow&&\color{red}\Large\downarrow&&&\color{red}\Large\downarrow&\color{red}\Large\downarrow \\
 \large{bitmask}&\Large0&\Large1&\Large0&\Large1&\Large0&\Large0&\Large1&\Large1 \\
 \hline
 \large{result}&\Large1&\Large0&\Large0&\Large1&\Large1&\Large0&\Large1&\Large0 \\
 \hline
 \end{array}
$$

## One's Complement
The one's complement of a byte inverts every bit in the operand. This is done by taking the bitwise NOT of the byte. Similarly, we can subtract the byte from 0xFF to get the one's complement.

## Two's Complement
The two's complement of a byte is the one's complement of the byte plus one. Therefore, we can apply the bitwise NOT of the byte, and then add one to it.

## Shifts
Shifts are used to move bits within a byte. In many programming languages this is represented by two greater than >> or two less than << characters. 

i.e. $a\gg s$ will shift the bits in $a$ by $s$ places to the right while adding 0's to the MSB.

![[Pasted image 20230316194915.png]]

Similarly, $a\ll s$ will shift the bits in $a$ by $s$ places to the left while adding 0's to the LSB. 
![[Pasted image 20230316194939.png]]

When using [[Signed-Integers]], the arithmetic shift is used to preserve the value of the sign bit when shifting.
![[Pasted image 20230316195010.png]]

Left shifts are used to multiply numbers by 2 (if no overflow), whereas right shifts are used to divide numbers by 2 (for unsigned integers).

## Roatations
Rotations are used to shift bits with a carry from the previous [[Instructions|Instruction]].
**Rotate left (rol):**
- Shifts all bits to the left, shifts carry bit into LSB and shifts MSB into carry bit
![[Pasted image 20230316195040.png]]
**Rotate right (ror):**
- Shifts all bits to the right, shifts carry bit into MSB, and shifts LSB into carry bit
![[Pasted image 20230316195059.png]]
Here the blue bit is carried from the previous instruction, and the carry bit is updated to the value of the bit that was shifted out. Rotations are used to perform multi-byte shifts and arithmetic operations