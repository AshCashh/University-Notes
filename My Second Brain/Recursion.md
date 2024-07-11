---
aliases:
  - Recursive
tags: [cs]
Created: 2024-03-12T22:10:29+10:00
Modified: 2024-07-03T19:35:33+10:00
---
In [[Computer Science]], recursion is a method of solving a [[Computation|Computational]] problem where the solution depends on solutions to smaller instances of the same problem. When defining a type of object, it is sometimes easiest to define it in terms of itself. This is known as a recursive definition.

### Example 
The factorial function on $\mathcal{N}$ can be defined by:
$$n!=\prod_{j=1}^{n}j=1\cdot2\dots(n-1)\cdot n$$
We ca also define $n!$ recursively by:
$$f(n)=\begin{cases} \space1 & : n=1\\
 \space n(n-1)!& :n>1 \\
\end{cases}
$$