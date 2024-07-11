---
tags: [logic, cs]
Created: 2024-05-04T18:10:55+10:00
Modified: 2024-07-03T19:35:33+10:00
---
In [[Computer Science]], and language theory, a regular language (also known as rational language) is a formal language that can be defined by a regular expression.

Alternatively, a regular language can be defined as a language recognised by a finite automaton. The equivalence of regular expressions and finite automata is known as Kleene's theorem. 

These can be defined by a few rules such as, there exists no other regular languages other than the following: 
- $\emptyset$ and $\{\epsilon\}$ are regular languages
- For each $a\in\sum\limits$ we can say that $\{a\}$ is a regular expression
- If $A$ and $B$ are said to be regular languages, than any combination of them be it $A\cup B, A\cdot B$ or $A^*$ are all regular languages
Some examples of regular languages could be:
- A set of IP addresses in some format (e.g. 192.168.1.1)
- A set of legal email addresses (following some format)
- A set of valid dates in DD-MM-YYYY format
# Symbols and Alphabets
We first start with some [[Set Theory|Set]] of symbols $\sum\limits\neq \emptyset$ which we call the alphabet. The alphabet is the set $\sum\limits$ and the elements represent the symbols. These symbols can be anything, e.g.:
- $\{0,1\}$, $\{a,b,c,\dots,z\}$, set of all principle ASCII characters, set of all UNICODE characters
We can then say a string over $\sum\limits$ is a sequence of symbols in $\sum\limits$. 
- We sometimes call these string words
- Starting from left where the first index is $1,x_j$ will refer to the $j$th symbol in $x$.
- The length of a string is the number of symbols in the sequence
- A string of length $0$ is called an empty string. We denote this with the $\epsilon$ symbol.
- The set $\sum\limits*$ (The Kleene star) is the set of all strings over $\sum\limits$ of any length.
Much like with bit-strings we can concatenate two strings together.
- $x=s_1s_2\dots s_j\in\sum\limits*$ 
- $y=t_1t_2\dots t_j\in\sum\limits*$
- $xy=s_1,s_2,\dots s_jt_1t_2\dots t_k$
A more practical example could show:
$$\begin{align}
x=abc\space \space y=123\\
xy=abc123
\end{align}
$$
# Languages
A language over an alphabet $\sum\limits$ is a set of strings over $\sum\limits$. In other words, a language $L$ is any subset $L\subseteq\sum\limits*$. We can specify a language in two different ways.
1. We can write out the language explicitly:
$$L=\{1,11,111,1111\}$$
2. Or we can write out rules for the strings the language contains:
$$L=\{x\in\{0,1\}*:x_1=1\}$$
## Decision Problems
For every language $L$ there exists a problem called the decision problem. This problem is all about deciding whether a given string $x\in\sum\limits*$ is in $L$ or not. We can phrase any computation problem with a yes or no answer as a decision problem.

## Language Operations
Due to languages being at their core being sets, we can apply operations on them such as $\cup$ or $\cap$. We can also concatenate languages by simply pairwise concatenating all their elements.
$$A\cdot B:=\{ab:a\in A,b\in B\}$$
Let's see an example of this, let:
$$A=\{0,1\},\space B=\{a,b\}$$
Then:
$$\begin{align}
A\cdot B&=\{0a,0b,1a,1b\}\\
A\cdot A&=\{00,01,10,11\}\\
A\cup B&=\{0,1,a,b\}
\end{align}
$$
# Kleene Star
We call the Kleene start of a language $A$ as the set of all possible concatenations of any length of strings from A.
- $A^0:=\{\epsilon\}$
- $A^1:=A$
- $A^j:=A^{j-1}\cdot A$
- $A^*:=A^0\cup A^1\cup A^2\cup\dots$
The Kleene plus is similar to the Kleene star except we omit the empty string.
$$A^+:=A^1\cup A^2\cup A^3\cup\dots$$
