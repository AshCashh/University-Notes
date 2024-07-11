---
aliases:
  - Set
  - Sets
tags: [logic, math]
Created: 2024-03-15T11:46:19+10:00
Modified: 2024-07-03T19:35:33+10:00
---
Set theory is the branch of [[Mathematical Logic]] that studies sets, which can be informally described as collections of objects. Although objects of any kind can be collected into a set, set theory as a branch of [[Mathematics]] is mostly concerned with those that are relevant to mathematics as a whole.

# Sets
A set is a mathematical model for a collection of different things; a set contains elements or members which can be mathematical objects of any kind: numbers, symbols, points in space, lines or geometrical shapes, variables or even other sets. A set with no elements is the empty set; a set with a single element is a singleton. A set may have a finite number of elements or be an infinite set.

We can define sets by:
Listing elements:
$$\text{Small Primes} = \{1,2,3,5,7\}$$
Set builder notation:
$$\text{Squares}=\{x\in\mathcal{Z}:x=y^2\text{ for some } y\in\mathcal{Z}\}$$
### Sets Examples
$$\begin{align}
\text{Integers: }Z&=\{...-2,-1,0,1,2,\dots\}\\
\text{Positive Integers: }Z^{+}&=\{1,2,3,\dots\}\\
\text{Non-negative Integers}=Z_{\geq0}&=\{0,1,2,3,\dots\}\\
\text{Rationals: }Q&=\left\{\frac{x}{y}:x,y\in Z\right\}\\
\text{Real numbers (decimals): }&\mathbb{R}\\
\text{Set of numbers 1 through n: }[n]&=\{1,\dots,n\}\\
\{x\in\mathbb{Z}:x|60\}
\end{align}
$$
Sets don't have to be numbers! Some more sets:
$$\begin{align}
\text{Empty set (no element): }&\emptyset=\{\}\\
\text{Set of students in CAB203}&\\
\{\text{Apple, Organge, Banana}\}&\\
\text{Sets don't have to be the same type: }&\{\text{apple},\sqrt{2},\emptyset\}\\
\text{Sets can include other sets: }&\{\{1\},2,\emptyset\}
\end{align}
$$
### Equity of Sets
Two sets are considered to be equal if they contain the same elements: i.e. $S=T$ when:
$$\text{Every element }x\in S\text{ is in }T$$
$$\text{Every element }x\in T\text{ is in }S$$
### Size of Sets
The size of a set is noted like $|S|$, and counts the number of distinct elements in the set:
$$\begin{align}
|\{1,2,3\}|=3\\
|\{1,1,1\}|=1\\
|\{♣, ♢, ♡, ♠\}|=4
\end{align}
$$
The size of infinite sets, like $\mathbb{Z}$ are counted using cardinal numbers, which are generalisation of $\mathbb{Z}^+$. 
# Membership
If $B$ is a set and $x$ is an element of $B$, this is written in shorthand as $x\in B$, which can also be read as "x belongs to B", or "x is in B". The statement "y is not an element of B" is written as $y\not{\in}B$, which can also be read as "y is not in B".                           

### Membership Examples
- $15\in\{1,3,5,\dots\}$ Because it follows the implied condition (odd numbers)
- $1\in\{1,2,3\}$ Because it i sin the explicit list
- $12\in\{x\in\mathbb{Z}:x|60\}$ Because 12 is an integer and 12 divides 60

Why are implied conditions bad?
- Maybe $6\in\{2,4,\dots\}$ Because it follows the implied condition (even numbers)
- Maybe $6\in\{2,4\dots\}$ Because it does not follow the implied condition (powers of 2)
We can interpret the pattern in multiple ways, so there is no unique answer to this question. Therefore we should avoid implied sets.

# Subsets
We say that A is a subset of B if every $x\in A$ is in B. We write:
$$A\subseteq B$$
A proper subset is a subset that is not equal to its parent set. That is to say, $A$ is a proper subset of $B$ if $A$ does not equal to $B$.
$$A\subset B$$
Note: $A\subset B\equiv A\subseteq B\wedge A\neq B$  

The subset of all subset of a set $S$ is called the power set of $S$, written $P(S)$.
$$P(\{1,2\})=\{\emptyset\,\{1\},\{2\},\{1,2\}\}$$
### Subset Examples
$$\begin{align}
&\text{For any set }S,\emptyset \text{ and S are subsets of S}\\
&\{1,2,3\}\text{ is a proper subset of }\{1,2,3,4,5\}\\
&\mathbb{Z}^2\subset \mathbb{Z}\\
&\{2x:x\in\mathbb{Z}\}\subset\mathbb{Z}\\
&\{1,2,3\} \text{ is not a subset of }\{2x:x\in\mathbb{Z}\}\\
&\{\text{apple,banana}\}\text{ is a subset of }\{\text{apple,carrot,banana}\}\\
\end{align}
$$

# Universe Sets
A universe $\mathit{U}$  is a collection that contains all the entities one wishes to consider in a given situation. Universes are often classes that contain (as elements) all sets for which one hopes to prove a particular theorem.

Allow us to define complements:
$$\overline{S}=\{x\in\mathit{U}:x\not{\in}S\}$$
Examples with $\mathit{U}=\mathbb{Z}^2$:
$$\text{Composites}=\overline{\text{Primes}}$$
$$\text{Evens}=\{x:x=2y\}$$
# Characteristic Vectors
Assuming our universe isn't too big we can represent our sets as bit-strings, also known as characteristic vectors. So we can say:
- Let $n=|\mathit{U}|$ (let n equal the size of our universe)
- Each element of $\mathit{U}$ is given a number such that $\mathit{U}=\{e_1,e_2,\dots,e_n\}$
- $\mathcal{X}_S=\mathcal{X}_{S_1},\mathcal{X}_{S_2},\dots,\mathcal{X}_{S_n}, \text{where}$ 
$$\mathcal{X}_{S_j}=\begin{cases} 0&e_j\not{\in}S\\
 1&e_j\in S
\end{cases}
$$
So let's see a few examples of this with our universe defined such that $\mathit{U}=\{1,2,3,4,5\}:$
- $\mathcal{X}_{\{1,3,4,5\}}=$ `0b10111`
-  $\mathcal{X}_{\{1,3,5\}}=$ `0b10101`
-  $\mathcal{X}_{\{3\}}=$ `0b00100`

## Numbers
| Name       | Symbol                                                                   | Example                                               |
| ---------- | ------------------------------------------------------------------------ | ----------------------------------------------------- |
| Integers   | $\mathbb{Z}$ All positive and negative whole numbers                     | $\{\dots,-1,-2,0,1,2,\dots\}$                         |
| Natural    | $\mathbb{N}$ All positive integers                                       | $\{0,1,2,\dots\}$                                     |
| Real       | $\mathbb{R}$ All numbers, including floating point                       | $\{\frac{1}{5},\sqrt{\frac{1}{5}},0,-2\}\}$           |
| Rational   | $\mathbb{Q}$ All real numbers as fractions                               | $\{\frac{1}{5},\frac{5}{1},\frac{2}{3},\frac{3}{2}\}$ |
| Irrational | $\mathbb{I}$ All real numbers that are not fractions                     | $\{\pi,\sqrt{2},\sqrt{3}\}$                           |
| Imaginary  | NA Numbers which are the product of a real number and the imaginary unit | $\{3i,-5i,3\sqrt{2}i\}$                               |
| Complex    | $\mathbb{C}$ All numbers which can be expressed in the form: $a+bi$      | $\{1+2i,1,i,-3i,0,}                                   |
 ![[Pasted image 20240407110039.png|centre|500]]
 