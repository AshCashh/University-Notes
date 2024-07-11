---
tags: [logic, math]
Created: 2024-03-24T14:48:51+10:00
Modified: 2024-07-03T19:35:33+10:00
---
A mathematical proof is a deductive argument for a [[Mathematics|Mathematical]] statement, show that the stated assumptions [[Mathematical Logic|Logically]] guarantee the conclusion. That is to say, a proof is a list of steps mathematically showing a statement is correct. A proof starts with some premises and ensures all other formulas on the proof are:
- [[Logical Equivalence|Logically Equivalent]] to the formula above it
- [[Logical Implication|Logically Implied]] by a formula above it
- Is the AND ($\wedge$) of some formula above it
- Or both Logically implied by the AND of some formulas above it

A proof produces a new logical implication $P \vDash Q$ where:
- $P$ is the AND of all the premises
- $Q$ is the last line of the proof
A proof says that, assuming all the premises are true, the conclusion is also true.

## Example
Let's prove a Socrates example:
- 'Socrates is mortal or is not human'                 ($M\vee\neg H$)
- 'Socrates is human'                                             ($H$)
We can conclude:
- Socrates is not human or socrates is mortal  ($\neg M\vee M$) 
- 'Socrates is mortal'                                             ($M$)

Or in proper notation:
$(M\vee \neg H)\wedge H\vDash M$:

| Line Num | Formula         | Description                              | Using Statement                                        |
| -------- | --------------- | ---------------------------------------- | ------------------------------------------------------ |
| 1        | $M\vee \neg H$  | Premise                                  | -                                                      |
| 2        | $H$             | Premise                                  | -                                                      |
| 3        | $\neg H \vee M$ | Equivalent to Line 1                     | $A\vee B\equiv B\vee A$                                |
| 4        | $\neg\neg H$    | Equivalent to Line 2                     | $A\equiv \neg\neg A$                                   |
| 5        | $M$             | Logical Implication of Line 3 AND line 4 | $(A\vee B)\wedge  A\vDash B$ with $A=\neg H$ and $B=M$ |
$$
\begin{array} {cc}
M\lor\neg H \\
H\\
\hline 
\neg H\lor M \\ 
\neg\neg H \\ 
(\neg H\lor M)\land H\\
M
\end{array}
$$
## Example 2
