---
tags: [cs, ee]
Created: 2024-03-01T19:44:02+10:00
Modified: 2024-07-03T19:35:33+10:00
---
In [[Computer Science]], encoding is the process of converting data into a format required for a number of information processing needs, including Program compiling and execution, Data transmission, storage and compression / decompression. In [[Electronics]] encoding refers to [[Analogue to Digital Conversion]]. Examples of use of encoding include Lexicographic ordering, [[ASCII]] and [[Unicode]].
#### Example
Let's encode the set of characters $\{a,f,z,7\}$ in 2-bit strings:
$$ \begin{array} {cc} 
\hline \text{String}  & \text{ Character }\\ 
\hline 00 & \text{z} \\ 
01 & \text{a} \\
10 & 7 \\
11 & \text{f} \\
\hline 
\end{array} 
$$
This isn't a very good encoding. The set of character isn't useful, there is no logical ordering and different types of characters are mixed together.

## Lexicographic Ordering
A common way of ordering [[Binary|bit]] strings is *lexicographic ordering*. This is like alphabetical ordering where compare strings are done one bit at a time from left to right.
#### Examples
- 000 comes before 100 (like bat comes before cat)
- 000 comes before 001 (like are comes before art)
- 011 comes before 100 (like bzz comes before caa)
- 01 comes before 010 (like at comes before at)


