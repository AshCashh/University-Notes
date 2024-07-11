---
tags: [logic, math]
Created: 2024-03-20T20:33:37+10:00
Modified: 2024-07-03T19:33:56+10:00
---
A syllogism is a kind of logical argument that applies deductive reasoning to arrive at a conclusion based on two [[Propositional Logic|Propositions]] or premises that are asserted or assumed to be true. If the premises are true, then it is logically impossible for the conclusion to be false.  
## Example
$$
\begin{array} {cc}
\text{All humans are mortal (major premise)} \\
\text{Socrates is human (minor premise)}\\
\hline 
\text{Socrates is mortal (conclusion)}

\end{array}
$$
#### [[Set Theory]] Notation
We can frame syllogisms in set-theoretic language.
$$
\begin{array} {cc}
\text{Humans}\subseteq\text{ Mortals} \\
\text{Socrates} \in \text{Humans}\\
\hline 
\text{Socrates}\in\text{ Mortals}

\end{array}
$$
![[Pasted image 20240320204207.png|centre|200]]
# Types
### Valid
We can abstract the argument to a syllogism type:
$$
\begin{array} {cc}
A\subseteq B \\
x \in A\\
\hline 
x\in B

\end{array}
$$
This is a **valid type** meaning that it works for any $A,B,x$ as long as the premises are true.
### Invalid
Most argument types are not valid:
$$
\begin{array} {cc}
x\in A\cap B \\
y \in B\\
\hline 
y\in A
\end{array}
$$
$$
\begin{array} {cc}
\text{Einstein was a genius and a physicist} \\
\text{I am a physicist}\\
\hline 
\text{I am a genius}
\end{array}
$$
$$
\begin{array} {cc}
\text{Many flowers smell nice} \\
\text{Rafflesia is a kind of flower}\\
\hline 
\text{Rafflesia smells nice}
\end{array}
$$
### Invalid Type but Correct Conclusion
An invalid argument does not mean the conclusion is wrong.
$$
\begin{array} {cc}
\text{All humans are mortal} \\
\text{Socrates is moral}\\
\hline 
\text{Socrates is human}
\end{array}
$$
It happens that Socrates was human, but this is an invalid form. Same form with different premises:
$$
\begin{array} {cc}
\text{All mothers are mortal} \\
\text{Socrates is moral}\\
\hline 
\text{Socrates is a mother}
\end{array}
$$
There are 24 other valid types out of 256 possible syllogism types.

## More Examples
$$
\begin{array} {cc}
\text{All mothers are females} \\
\text{Some humans are mothers}\\
\hline 
\text{Some humans are females}
\end{array}
$$
$$
\begin{array} {cc}
M\subseteq F \\
H\cap M\neq \emptyset\\
\hline 
H\cap F\neq \emptyset\\
\end{array}
$$
---
$$
\begin{array} {cc}
\text{All trees have leaves} \\
\text{The oak in my yard is a tree}\\
\hline 
\text{The oak in my yard has leaves}
\end{array}
$$$$
\begin{array} {cc}
\forall x\in T p(x) \\
t\in T\\
\hline 
p(t)\\
\end{array}
$$
Explanation: $Tp(x)$:  $=x$ has leaves, $t=$ oak in my yard.
Hence: $(\forall x\in Tp(x))\land(t\in T)\vDash p(t)$

------
$$
\begin{array} {cc}
\text{All cats are mammals} \\
\text{Cats have live young}\\
\hline 
\text{Some mammals have live young}
\end{array}
$$
$$
\begin{array} {cc}
A\subseteq B\text{ and } A\neq \emptyset \\
A \subseteq C\\
\hline 
B \cap C\neq \emptyset\\
\end{array}
$$
Valid

---
$$
\begin{array} {cc}
\text{All canines are mammals} \\
\text{My cat is a mammal}\\
\hline 
\text{My cat is a canine}
\end{array}
$$
$$
\begin{array} {cc}
A\subseteq B\\
x\in B\\
\hline 
x\in A\\
\end{array}
$$
Invalid
