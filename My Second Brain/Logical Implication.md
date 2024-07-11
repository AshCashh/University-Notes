---
tags: [logic]
Created: 2024-03-22T20:38:25+10:00
Modified: 2024-07-03T19:35:33+10:00
---
Logical Implication is the process of deriving a true [[Propositional Logic|Proposition]] from another true proposition. We can represent logical implication using the notation:
$$A\vDash B \space\space\space (\text{From A, conclude B}) $$
Which states that every instance when $A$ is true, so is $B$. But $B$ can be true without $A$. Hence $A$ implies $B$.

This is equivalent to saying that $A\to B$ is a [[Tautology]]. It's important to note that logical implication aren't symmetrical and we can always make substitutions. We only substitute using logical implication if the left hand side is known to be true.

There are two general ways that we can find logical implications, either through truth tables or the use of proofs. When using a TT we can prove that $A\vDash B$ by checking every line where $A=T$ that $B=T$.

## Examples
From: $A\vee B$, we can conclude that $A$ is true ($A\lor B\vDash A$):
$$ \begin{array} {cc} \hline A & B & A\lor B\\ \hline 0 & 0 & 0\\ 0 & 1 & 1\\ 1 & 0 & 1\\ 1 & 1 & 1\\ \hline \end{array} $$
But $A\lor B\vDash B$ is incorrect, because of the third line where $A\lor B$ is true but $B$ is false.
From $(A\to B)\wedge A$ we can conclude that B is true.
$$\begin{align}
&A\wedge B\vDash A\\
&A\vDash A\vee B\\
&(A\to B)\wedge A\vDash B\\
&(A\to B)\wedge(A\to C)\vDash A \to C \\
&(A\vee B)\wedge\neg A \vDash B

\end{align}
$$
# Using Logical Implication
Unlike [[Logical Equivalence]], it is not always safe to make substitutions with logical implications
- Safe example: Substituting an entire formula which is known to be true. We have $A\wedge B\vDash A$ so if $A\wedge B$ by itself is true, it can be replaced with $A$
- From 'It is cloudy and rainy'. We can conclude it is raining
### Unsafe Use
In general we cannot substitute into a formula using logical implications:
- Unsafe example: Use $A\wedge B\vDash A$ and substitute into $\neg(A\wedge B)$ to get $\neg A$. This does not work
- From 'NOT (Socrates is human and a teapot)'. We cannot conclude 'Socrates is not human'.

Only substitute using a logical implication if the left hand side is known to be true. This is guaranteed by the rules of proofs.

# Predicates
Just as we'd suspect all previous logical implications also work with [[Predicate Logic|Predicates]]. Here are some examples:
- $(\forall x\in Sp(x))\land(y\in S)\vDash p(y):$ All humans are mortal and Socrates is human implies Socrates is mortal
- $p(x)\land(x\in S)\vDash \exists y\in Sp(y)$: Socrates is male and human implies there exists some human who is male
- $(\forall x\in Sp(x))\land(S\neg \emptyset)\vDash\exists y\in Sp(y)$: All humans are mortal and there exists humans implies there exists a human is mortal 