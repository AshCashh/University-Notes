---
aliases:
  - Binary Digit
  - bit
  - bits
tags:
  - cs
Created: 2024-03-01T00:00:00+10:00
Modified: 2024-07-03T19:35:33+10:00
---
In [[Mathematics]] and in [[Computer Science]], a binary digit or bit, is the smallest unit of data. Each bit has a single value of either 1 or 0, which means it can't take on any other value.

A sequence of 8 bits is known as a byte, and it is the most common representation of data in digital systems. A sequence of 4 bits is known as a nibble. A sequence of n bits can represent up to $2^n$ states.

## Binary Representation 
The binary system is a base-2 system that uses a sequence of bits to represent a number. Bits are written right-to-left from least significant to most significant bit.
- The **least significant bit** (LSB) is at bit index 0.
- The **most significant bit** (MSB) is at bit index n-1 in an n-bit sequence.

$0000_2 =0$       $0001_2=1$       $0010_2=2$       $0011_2=3$       $0100_2=4$       $0101_2=5$       $0110_2=6$       
$0111_2=7$       $1000_2=8$       $1001_2=9$       $1010_2=10$     $1011_2=11$     $1100_2=12$     $1101_2=13$     $1110_2=14$     $1111_2=15$

Note: the subscript 2 indicates that the number is represented using a base-2 system
### Data as Bits
Some types of data representation include:
- Characters
- String of characters (text)
- Integers
- Decimal numbers (floats)
Most other types of data are converted to numbers or strings or some larger structure with numbers and text inside.
### Characters as Bits 
Characters are just symbols. Some types:
- Symbols from writing systems (e.g. Latin letters, devanagari letters, symbols from Kanji)
- Numerals
- Diacriticals (accents)
- Punctuation (. , ; : ")
- Mathematical symbols 
- Braille symbols
- Whitespace characters (space, tab, etc)
Representing characters as bit strings is done using [[Encoding]], which requires: 
- A set of characters to represent (e.g. the Latin alphabet)
- A length $n$ for our bit strings
- A mapping from characters to $\{0,1\}^n$
## Bit Strings
We usually use many bits together in *strings*. The notation consists of the following:
- A bar over a variable indicates a string: $\bar{x}$ 
- The set of all strings of length $n$ is $\{0,1\}^n$ (also called $n$-bit strings)
- All bit strings of all lengths are members of $\{0,1\}^*$ 
- The $j$th bit in $\bar{x}$ is $\bar{x}_j$ (j goes from 0 to $n-1$)
- For bit string we most often count from the right, so $\bar{x}_0$ is the furthest to the right (MSB)

### Concatenation
We can also concatenate bit strings, which joins them together. If $\bar{x}$ is an $n$-bit string and $\bar{y}$ is a $m$-bit string, then $\bar{z}=\bar{xy}$ is a $(n+m)$-bit string.
Example: $\bar{x}=000$ and $\bar{y}=11$, then $\bar{xy}=00011$.

Concatenation is sometimes written like $\bar{x}||\bar{y}$ or $\bar{x}\cdot\bar{y}$.
