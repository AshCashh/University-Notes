---
tags: [logic]
Created: 2024-03-24T14:16:13+10:00
Modified: 2024-07-03T19:35:33+10:00
---
# Logically Equivalent Formulas
In [[Propositional Logic]] two formulas are logically equivalent if they both have the same truth value. For example, $A\to B$ is equivalent to $\neg A\vee B$ as they both have the same truth values.

Let's create a truth table to prove it they are both equivalent:
$$ 
\begin{array} {cc} 
\hline A  & B & \neg A & A\to B & \neg A \vee B\\ 
\hline T & T & F & T & T\\ 
 T & F & F & F & F\\
 F & T & T & T & T\\
 F & F & T & T & T
\end{array} $$Here the last two columns are identical. Therefore: $A\to B\equiv \neg A\vee B$.
Logically equivalent formula examples:
- $\neg\neg A\equiv A$
- $A\wedge B\equiv B\wedge A$
- $A\vee B\equiv B\vee A$ 
- $A\vee \neg A\equiv T$
- $A\wedge\neg A\equiv F$ 
- $A\land T\equiv A$
- $A\lor F\equiv A$
- $A\wedge(B\wedge C)\equiv(A\wedge B)\wedge C$
- $A\vee(B\wedge C)\equiv(A\vee B)\wedge (A\vee C)\equiv B\lor (A\lor C)$ 
- $A\land(A\lor C)\equiv(A\land B)\lor(A\land C)$
- $A\lor B\equiv \neg(\neg A\land \neg B )$
- $A\land B\equiv\neg(\neg A\lor \neg B)$
- $A\to B\equiv \neg A\lor B$
- $\neg A\to T\equiv T$
- $A \leftrightarrow B\equiv (A\to B)\land(B\to A)$
## Using Logically Equivalent Formulas
We can do substitution whenever we have two logically equivalent formulas: replace an occurrence of a formula with the thing it is equivalent to:
- Suppose $A\equiv B$. Then substituting in $B$ for $A$ in $A\vee C$ we get:
$$A\vee C\equiv B\vee C$$
Also:
- If $A\equiv B$ and $B\equiv C$ then $A\equiv C$  

# Predicates
Just as for Boolean formulas, we have equivalences for [[Predicate Logic|Predicates]]:

| Predicate:                                                                                                                       | Explanation                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| $\neg(\forall x \space p(x))\equiv\exists x\neg p(x)$                                                                            | It is not the case that all humans are male is equivalent to saying there exists some human which is not male |
| $\neg(\exists x\space p(x))\equiv \forall x\neg p(x)$<br>Alternative:<br>$\neg(\exists  x\space \neg p(x))\equiv \forall x p(x)$ | It is not the case that there exists a human which can fly is equivalent to saying all humans can't fly.      |
| $\forall x(p(x)\land q(x))\equiv(\forall xp(x))\land(\forall xq(x))$                                                             |                                                                                                               |
| $\exists x(p(x)\lor q(x))\equiv(\exists xp(x))\lor (\exists xq(x))$                                                              |                                                                                                               |

- $\neg(\forall x \space p(x))\equiv\exists x\neg p(x)$: It is not the case that all humans are male is equivalent to saying there exists some human which is not male
- $\neg(\exists x\space p(x))\equiv \forall x\neg p(x)$: It is not the case that there exists a human which can fly is equivalent to saying all humans can't fly.
- $\forall x(p(x)\land q(x))\equiv(\forall xp(x))\land(\forall xq(x))$
- $\exists x(p(x)\lor q(x))\equiv(\exists xp(x))\lor (\exists xq(x))$
