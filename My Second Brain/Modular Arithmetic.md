---
tags: [math]
Created: 2024-02-27T19:37:18+10:00
Modified: 2024-07-03T19:35:33+10:00
---
In [[Mathematics]], modular arithmetic is a system of arithmetic for integers, wheres numbers "wrap around" when reaching a certain value, called the modulus. It is an [[Abstraction]] of [[Parity]] and clock arithmetic. We know parity uses modulo 2 as there can be 2 values, even or odd and we know that clocks use modulo 12 as there are only 12 hours on the clock. Therefore, modular arithmetic says we can have arithmetic modulo $n$ for any positive integer $n$.

Modular arithmetic works by replacing equality with modular equivalence, also called modular congruence. If $(a-b)\space |\space n$ then $a$ and $b$ are equivalent modulo $n$:
$$a\equiv b\tag{mod n}$$
What this means is 2 things have the same parity if their difference is divisible by $n$
#### Example
$$5\equiv3\tag{mod 2}$$
Here we see $5-3=2$ which is divisible by $2$ showing us that 5 and 3 have the same parity

## Properties
Modular arithmetic also plays nicely with addition, subtraction and multiplication. Let's look at an example using $a\equiv b+c\equiv d\space\text{(mod n)}$:
$$
\begin{align}
	&a+b\equiv b+d\tag{mod n}\\
	&a-c\equiv b-d\tag{mod n}\\
	&ac\equiv bd\tag{mod n}
	\end{align}


$$


