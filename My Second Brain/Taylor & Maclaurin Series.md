#math
[[Mathematics]]
# Infinite Series
## Sequences
A sequence is an ordered list of numbers: $a_1,a_2,a_3,\dots,a_n,\dots$
The sequence can be denoted by: $\displaystyle\{a_n\}_{n=1}^{\infty}$   
Where $a_n$ is the $nth$ term, or just $\{a_n\}$ 

##### Example
$$1,\frac{1}{2},\frac{1}{3},\frac{1}{4},\frac{1}{5},\dots$$
Here $a_n=\cfrac{1}{n},$ for $n=1,2,\dots$ or $\left\{\cfrac{1}{n}\right\}_{n=1}^{\infty}$   
$$1,-1,1,-1,1,-1,\dots$$
Here $a_n=(-1)^{n-1}$ or $\{(-1)^{n-1}\},$ for $n=1,2\dots$



### Limits of Sequences:
A sequence $\{a_n\}$ has the limit $L$ if $a_n$ approaches $L$ as $n$ approaches infinity. We write:
$$ \lim_{n\to\infty}a_n=L\space\text{or}\space a_n\to L \space \text{as} \space n\to \infty$$
If the limit exists we say that the sequence **converges**. That is when the limit is equal to a constant. 
Otherwise, we say the sequence **diverges**

The idea of the limit of sequences $\{a_n\}$ as $n\to\infty$ and the limit of a function $f(x)$ as $x\to\infty$ is essentially the same.

The only difference is that $n$ is an integer whereas $x$ is any real number.

Importantly, if $\displaystyle\lim_{n\to\infty}=L$ and $f(n)=a_n$ where $n$ is an integer, then:
$$\lim_{n\to\infty}a_n=L$$
This means that we can use our previous techniques for evaluating limits of functions to evaluate limits of sequences.

##### Example
$a_n=\cfrac{1}{n}$ converges to 0
##### Example 2
$a_n=(-1)^{n-1}$ oscillates, does not converge to a finite value as $n\to \infty$, so it diverges.
##### Example 3
$a_n=n$ diverges to infinity.

##### Example
Determine the limit of the sequence $\left\{\cfrac{4}{n^2}\right\}$ 
$$\cfrac{4}{1},\cfrac{4}{4},\cfrac{4}{9},\dots$$
Therefore,
$$\lim_{n\to\infty}\cfrac{4}{n^2}=0$$
Which converges to 0.
##### Example 2
Determine the limit of the sequences $\left\{\cfrac{3}{4}^n\right\}$ and $\left\{\cfrac{4}{3}^n\right\}$
$$\cfrac{3}{4},\cfrac{9}{16},\cfrac{27}{64},\dots$$
Therefore, the sequence converges
$$\lim_{n\to\infty}\left\{\cfrac{3}{4}\right\}^n=0$$
and
$$\cfrac{3}{4},\cfrac{16}{9},\cfrac{64}{27},\dots$$
Therefore, the sequence diverges
$$\lim_{n\to\infty}\left\{\cfrac{4}{3}\right\}=\infty$$

 

## Series
Given a particular sequence $\{a_n\}$, we can formulate a sequence of sums,
$$\begin{align}
&S_1 = a_1 \\
&S_2 =a_1+a_2 \\
&S_2 = a_1 + a_2 + a_3 \\
&\;\;\vdots \\
&S_n = a_1+a_2+a_3+\dots+a_n 
\end{align}$$
The new sequence $\left\{S_n\right\}$ is called the sequence of **partial sums**.

If $\left\{S_n\right\}$ converges, that is $\displaystyle\lim_{n\to\infty}S_n=L$, where $L$ is a finite value, then we say that the infinite series $\displaystyle\sum_{i=1}^{\infty}a_i$ converges.

If a series does not converge, then it diverges (approaches infinity).

### Geometric Series
The geometric series:
$$\sum_{n=0}^{\infty}ar^n=a+ar+ar^2+\dots$$
is convergent if $|r|<1$ and diverges if $|r|\geq 1$.

If $|r|<1$, we have
$$\sum_{n=0}^{\infty}ar^n=\cfrac{a}{1-r}$$
### Harmonic Series
The harmonic series:
$$\sum_{n=1}^{\infty}\cfrac{1}{n}$$
is a special case to remember where it equals,
$$=1+\cfrac{1}{2}+\cfrac{1}{3}+\cfrac{1}{4}+\dots$$
which diverges (approaches infinity).

The harmonic series is a special case of the so-called $p$-series.
$$\sum_{n=1}^{\infty}\cfrac{1}{n^p},$$
which appears when we consider Fourier series.

If $0<p\leq 1$, the $p$-series diverges. E.g.,
$$\sum_{n=1}^{\infty}\cfrac{1}{n^{1/2}}=1+\cfrac{1}{\sqrt{2}}+\cfrac{1}{\sqrt{3}}+\cfrac{1}{2}+\dots \text{diverges}$$
If $p>1$, the $p$-series converges. E.g.,
$$\sum_{n=1}^{\infty}\cfrac{1}{n^{2}}=1+\cfrac{1}{4}+\cfrac{1}{9}+\cfrac{1}{16}+\dots=\cfrac{\pi^2}{6},$$
$$\sum_{n=1}^{\infty}\cfrac{1}{n^{4}}=1+\cfrac{1}{16}+\cfrac{1}{81}+\cfrac{1}{256}+\dots=\cfrac{\pi^4}{90}.$$
### Alternating Series
An alternating series has terms that have alternating signs $(+,-,+,-,\dots)$

##### Example
$$\sum_{n=1}^{\infty}\cfrac{(-1)^{n-1}}{n}=1-\cfrac{1}{2}+\cfrac{1}{3}-\cfrac{1}{4}+\cfrac{1}{5}\dots$$
## Ratio Test

Let $\displaystyle \sum_{n=1}^{\infty}a_n$ be an infinite series and
$$\rho = \lim_{n\to\infty}\left|\cfrac{a_{n+1}}{a_n}\right|$$
$$
\begin{align}
&\text{(1) if }\rho < 1, \sum_{n=1}^{\infty}a_n\space\text{converges} \\
&\text{(2) if }\rho > 1, \sum_{n=1}^{\infty}a_n\space\text{diverges} \\
&\text{(3) if }\rho =1, \text{inconclusive}\\


\end{align}
$$
## Alternating Series Test
If the series $\displaystyle\sum_{n=1}^{\infty}(-1)^{n-1}a_n$ satisfies 
$$\begin{align}
&\text{(1)}\space a_n>0\space\text{for all}\space n\geq 1 \\
&\text{(2)}\space a_{n+1}\leq a_n \space \text{for all}\space n\geq 1\space (\{a_n\}\space \text{is decreasing}) \\
&\text{(3)}\lim_{n\to\infty}a_n=0

\end{align}
$$
then the series converges.
### Example
Does $\displaystyle\sum_{n=1}^{\infty}\cfrac{(-1)^{n-1}}{n}$ converge or diverge?

Let $a_n=\cfrac{1}{n}$. Then
- $

## Other
### Factorial Rules
$$
\begin{align}
n!&=n\times(n-1)\times(n-2)\times\dots\times 2\times 1 \\
\therefore (n+1)!&=(n+1)\times n\times(n-1)\times\dots 2\times 1 \\
&=(n+1)n!

\end{align}
$$
$$\cfrac{(n-1)!}{n!}=\cfrac{(n-1)(n-2)!}{n(n-1)(n-2)}=\cfrac{1}{n}$$
### Common Limits
$$\lim_{n\to\infty}\left(\cfrac{n}{n+k}\right)^n=e^{-k}$$
$$\lim_{n\to\infty}\left(1+\cfrac{k}{n}\right)^n=e^k$$


