---
aliases:
  - Propositional
  - Proposition
tags: [logic, cs, math]
Created: 2024-03-11T20:55:53+10:00
Modified: 2024-07-03T19:35:33+10:00
---
A proposition is the basic building block of [[Mathematical Logic|Logic]]. It is defined as a declarative sentence that is either True or False but not both. In [[Computer Science]] and [[Mathematics]] we build complicated and large propositions with the use of [[Logical Operators]] where True or T is denoted as 1 and False or F is a 0. 

We often use symbols like $p, q$, etc to stand in for propositions:
- $p = \text{I like tomatoes}$

# Atomic vs Compound Propositions
There are two different types of propositions: atomic and compound. Atomic propositions are ones that cant be broken down into more propositions. While compound propositions are made up of two or more atomic propositions. Here are a few examples:
- "The sun is shining" is atomic
- "If it is raining then I will go outside" is compound as it contains two propositions: "It is raining" and "I will go inside".

# Classifying Formulas 
There are three basic kinds of formulas, of which will always have the same behaviour no matter what truth tables we insert:
- [[Tautology|Tautologies]]: These formulas are always true
- [[Contradictions]]: These formulas are always false
- **Contingent Formulas**: These formulas are true or false depending on the variables
- **Satisfiable Formulas**: These formulas are either tautologies or contingent formulas

| Classification | Always True | Sometimes True | Always True |
| -------------- | ----------- | -------------- | ----------- |
| Tautology      | True        | False          | False       |
| Contradictions | False       | False          | True        |
| Contingent     | False       | True           | False       |
| Satisfiable    | True        | True           | False            |

# [[Logical Equivalence]] vs [[Logical Implication]]

| $P\equiv Q$                                                                                                                                                          | $P\vDash Q$                                                                                                                                                                |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| $P$ and $Q$ always have the same truth table, hence substitutions are allowed.<br><br>All rows in truth table are the same:<br>$P \leftrightarrow Q$ is a tautology. | $Q$ is true whenever $P$ is true.<br><br>Can only safe make substitutions when $P$ is true.<br><br>All rows where $P$ are $T$,$Q$ is also $T$: <br>$P\to Q$ is a tautology |
