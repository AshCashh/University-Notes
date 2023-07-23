#cs

In [[Mathematics]], sign/magnitude notation is the simplest and most obvious methods of encoding positive and negative numbers. Represented with a $+$ for positive numbers and $-$ for negative numbers.

However in [[Computer Science]], the sign-magnitude represents the most significant [[Binary|bit]], which encodes the sign of the integers. In an 8-bit sequence, the remaining 7-bits are used to encode the value of the bit.
- If the sign bit is 0, the remaining bits represent a positive value.
- If the sign bit is 1, the remaining bits represents a negative value.

As the sign bit consumes one bit from the sequence the range of values that can be represented by an n-bit sign magnitude encoded bit sequence is: $-(2^{n-1} - 1)$ to $2^{n-1}-1$.

For 8-bit sequences, this range is -127 to 127. This presents several issues:
1. There are two ways to represent zero: 0b10000000 = 0, or 0b00000000 = -0.
2. Arithmetic and comparison requires inspecting the sign bit.
3. The range is reduced by 1 (due to the reducant zero representation)
