#cs
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

## Bitwise Operations
When applying logical operators to a sequence of bits, the operation is performed in a bitwise manner. The result of each operation is stored in the coresponding bit index also.