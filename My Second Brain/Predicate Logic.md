---
aliases:
  - Predicate
tags: [logic]
Created: 2024-03-24T20:19:19+10:00
Modified: 2024-07-03T19:35:33+10:00
---
In [[Mathematical Logic|Logic]], a predicate is a [[Propositional Logic|Proposition]] that takes in one or more variables as arguments and returns a boolean value based on some logic using those arguments. For example, $P(x)\to\{T,F\}$ where $P$ is the predicate and $x$ is the parameter or argument taken by $P$. It's good to note that the variables we pass into predicates are different to the variables we pass into formulas. Predicate parameters can stand in for any value while variables in formulas stand in for propositions which must evaluate to either true or false.

We can use small predicates to form complex predicates just as we could with propositions due to predicates evaluating to a boolean value:
- $A(x)\land B(x)$
- $A(x)\to B(y)$
- $(A(x)\to B(y))\land A(x)$

## Truth Tables
Before we can evaluate the truth of a predicate we need to fill in the parameters with actual values:
- Suppose $A(x)$ is: $x^2=1$. Then $A(1)$ is true, but $A(2)$ is false
- Suppose $A(x)$ is: $x$ is a flower $\to x$ smells nice. Then $A(rose)$ is true, but $A(\text{reffelesia})$ is false.
- Suppose $A(x)$ is If $x$ is human, then $x$ is mortal. We might be tempted to say that $A(x)$ is true, but we can't because we haven't filled in $x$ yet.

Once we have filled in all variables in a predicate it becomes a regular proposition and hence has a truth value (true or false).

# Expressing Problems
The language of predicates allow us to precisely state problems:
- $x$ is prime $=\neg(\exists y, z\in \mathbb{N}((yz=x)\land(z\neq 1)))$ 
We can use logic to give an equivalent formulation:
$$\forall y,z\in\mathbb{N}((y=1)\lor(z=1)\lor(yz\neq x))$$
This suggests a simple algorithm:
- Loop through all $y,z\in\mathbb{N}$
- Check if $y=1,z=1$ or $yz\neq x$
Expressing our problem as a predicate gives explicit conditions that can be translated directly into program logic.

$$V=\{(u,v,r):((u,v)\in A)\}$$