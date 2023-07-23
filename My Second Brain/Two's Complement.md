#cs
In [[Computer Science]], the two's complement representation, the most significant [[Binary|bit]] encodes a negative weighting of $-2^{n-1}$. For example, in 8-bit sequences, index-7 represents a value of -128. The two's complement is calculated by adding 1 to the [[One's Complement]]. The range values are: $-2^{n-1}$ to $2^{n-1} - 1$ i.e. range of an 8-bit byte is: -128 to 127

This representation is more efficient than the previous because 
- There is a single representation for zero: 0b00000000
- Addition is exactly the same for a pair of two's complement integers as for a pair of unsigned integers.
- The range of numbers we can represent is increased by one compared with sign-magnitude or one's complement representation.
and subtraction is performed by adding the two's complement of the subtrahend. $a-b = a+(~b+1)$.

###### Examples:
$0111 1111 = 2^6+2^5+2^4+2^3+2^2+2^1+2^0 = 127$
$00001001=2^3+2^0=9$
$00000000=0$
$11111111=-2^7+2^6+2^5+2^4+2^3+2^2+2^1+2^0=-1$
$11111101=-2^7+2^6+2^5+2^4+2^3+2^2+2^0=-3$
$11111011=-2^7+2^6+2^5+2^4+2^3+2^1+2^0=-5$
$10001100=-2^7+2^3+2^2=-116$
$10000000=-2^7=-128