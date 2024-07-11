---
tags: [cs]
Created: 2023-06-27T14:15:42+10:00
Modified: 2024-07-03T19:35:33+10:00
---

A logical operator is a symbol or word used to connect two or more expressions such that the value of the compound expression produced depends only on that of the original expressions and on the meaning of the operator.

## Boolean Functions
A Boolean function is a function whose arguments and results assume values from a two-element set. These functions are also referred to as logical functions when they operate on [[Binary|bits]]. The most common logical functions available to microprocessors and most programming languages are:
- [[#Negation (NOT)|Negation]]: **NOT**
- [[#Conjunction (AND)|Conjunction]]: a **AND** b
- [[#Disjunction (OR)|Disjunction]]: a **OR** b
- [[#Exclusive Disjunction (XOR)|Exclusive Disjunction]]: a **XOR** b
By convention, we map a bit value of 0 to false, and a bit value of 1 to true.
We can describe any Boolean function using a truth table:
### Negation (NOT)
A unary operator used to invert a bit

$$ \begin{array} {cc} \hline a  & \text{ NOT }a\\ \hline 0 & 1 \\ 1 & 0 \\ \hline \end{array} $$
Typically written as: $NOT\space a$, $\sim a$, $\bar{a}$
### Conjunction (AND) 
AND is a binary operator whose output is true if both inputs are true.
$$ \begin{array} {cc} \hline a & b & a\text{ AND }b\\ \hline 0 & 0 & 0\\ 0 & 1 & 0\\ 1 & 0 & 0\\ 1 & 1 & 1\\ \hline \end{array} $$
Typically written as: $a\space AND\space b$, $a\space\&\space b$, $a \cdot b$, $a\wedge b$
### Disjunction (OR)
OR is a binary operator whose output is true or either input is true.
$$ \begin{array} {cc} \hline a & b & a\text{ OR }b\\ \hline 0 & 0 & 0\\ 0 & 1 & 1\\ 1 & 0 & 1\\ 1 & 1 & 1\\ \hline \end{array} $$
Typically written as: $a\space OR \space b$, $a\space|\space b$, $a+ b$, $a\vee b$    

### Exclusive Disjunction (XOR)
XOR (Exclusive OR) is a binary operator whose output is true if only one input is true
$$ \begin{array} {cc} \hline a & b & a\text{ XOR }b\\ \hline 0 & 0 & 0\\ 0 & 1 & 1\\ 1 & 0 & 1\\ 1 & 1 & 0\\ \hline \end{array} $$
Typically written as: $a\space XOR\space b$, $a\textasciicircum b$, $a \oplus b$

### IF... THEN
$a\to b$ signifies that $q$ must be true whenever $a$ is. However, when $a$ is false, $b$ can be whatever. When $a$ is false, then $a\to b$ is always true.
$$
 \begin{array} {cc} \hline 
 a & b & a\to b\\ \hline 
 0 & 0 & 1\\ 0 & 1 & 1\\ 
 1 & 0 & 0\\ 1 & 1 & 1\\ \hline \end{array} 
$$
### IF and only IF
$a \leftrightarrow b$ returns true if and only if $p$ and $q$ have the same truth value. This can also be written as $(a\to b)\wedge(b\to a)$ in long form.
$$
 \begin{array} {cc} \hline a & b & a\leftrightarrow b\\ \hline 0 & 0 & 1\\ 0 & 1 & 0\\ 1 & 0 & 0\\ 1 & 1 & 1\\ \hline \end{array} 
$$
$\forall v,u\in \space N(V, E, u)\cap N(V,E,v) \geq2$
