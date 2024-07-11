---
aliases:
  - Discrete Structures
tags: [logic, math]
Created: 2024-03-11T21:19:57+10:00
Modified: 2024-07-03T19:35:33+10:00
---
Discrete mathematics is the study of [[Mathematics|Mathematical]] structures that can be considered "discrete" rather than "continuous". Topics studied in discrete mathematics include integers, graphs and statements in [[Propositional Logic]]. By contrast, continuous mathematics such as real numbers, calculus or Euclidean geometry. 

# Week 3
[[Logical Operators]]
[[Propositional Logic]]
- [[Tautology]]
- [[Contradictions]]
[[Logical Equivalence]] ($\equiv$)
[[Recursion]] ($n!$)
# Week 4
[[Set Theory]]
- [[Set Operators]] ($\cap,\cup,\backslash$)
[[Syllogism]]
# Week 5
[[Logical Implication]] ($\vDash$)
[[Proofs]]
[[Predicate Logic]]
[[Quantifiers]]
# Week 6
[[Tuple]]
[[Cartesian Product]]
[[Relations]]
[[Functions#Logical Functions|Functions]]
# Week 7
[[Graphs]]
# Week 8
[[Trees]]
[[Directed Graphs]]
[[Flows]]

# Week 9
Case studies
# Week 10
[[Regular Language]]
[[Regular Expression]]



### Predicates, Parameters and Quantifiers
When we use quantifiers to specify parameters in predicates the values the quantifier is referring to can no longer be filled in with out own values. For example, in $\exists xP(x)$ the $x$ is filled in by $\exists x$ so we can't use our own value for $x$ anymore.

Due to predicates being able to take in more than one value we can sometimes end up having quantified parameters and free parameters (values that aren't quantified). In an instance like that, we can only use our own values for variables that haven't been quantified. Just remember, we can have multiple quantifiers in a statement but only one quantifier per value.

For example: $A(y)=\exists x P(x,y)$:
- $x$ is quantified over so we can't use our own values for it
- $y$ is not quantified over so we can fill it with our own values
- Due to $y$ not being quantified the truth value of $A(y)$ depends on the value of $y$

$x\in\mathbb{Z}\to x\in\mathbb{R}$: Is false and $x$ is a free parameter as it isn't quantified


# Tournament Structure
Two conditions need to be checked to ensure a tournament structure is valid:
1. For every pair of distinct players, either they play against each other, or there are at least two other players that they both play against.
2. All players have the same number of games.
