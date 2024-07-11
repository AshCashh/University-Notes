---
tags:
  - logic
Created: 2024-04-02T13:59:56+10:00
Modified: 2024-07-03T19:03:33+10:00
---
The cartesian product of two [[Set Theory|Sets]] $A$ and $B$ is a collection of pairs for every combination of $A$ and $B$. That is to say:
$$A\times B=\{(a,b):a\in A,b\in B\}$$
We then say the size of $A\times B$ is given by $|A\times B|=|A||B|$.

More generally we have:
Set products:
$$
A_1\times\dots\times A_n=\{(a_1,a_2,\dots,a_n:a_1\in A_1,\dots,a_n\in A_n\}
$$
Set powers:
$$
A^n=A\times A\times\dots\times A(\text{n copies of A})
$$
Set sizes:
$$|A_1\times\dots\times A_n|=|A_1|\dots|A_n|$$

### Example
$$
\begin{array}{ccc}
&A=\{a,b\}& B=\{1,2\}\\
\hline

\end{array}

$$
$$
\begin{array}{ccc}
&a&b\\
1&(a,1)&(b,1)\\
2&(a,2)&(b,2)
\end{array}

$$
$$
A\times B=\{(a,1),(a,2),(b,1),(b,2)\}
$$
### More Examples
- $\mathbb{R}^2$ describes points on a 2-dimensional plane
- $\{0,1\}^n$ is equivalent to the set of bit strings on length $n$
- $\text{KEYS}\times\text{VALUES}$ might describe the possible key-value pairs in a hash map.
- $\{0,\dots,1919\}\times\{0,\dots,1079\}$ encodes $(x,y)$ co-ordinates on a 1080p screen