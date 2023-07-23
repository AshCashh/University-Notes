## Infinite Series
#### Sequences
A sequence is an ordered list of numbers: $a_1,a_2,a_3,\dots,a_n,\dots$
The sequence can be denoted by: $\{a_n\}_{n=1}^{\infty}$   
Where $a_n$ is the $nth$ term, or just $\{a_n\}$ 

##### Example
$$1,\frac{1}{2},\frac{1}{3},\frac{1}{4},\frac{1}{5},\dots$$
Here $a_n=\cfrac{1}{n},$ for $n=1,2,\dots$ or $\left\{\cfrac{1}{n}\right\}_{n=1}^{\infty}$   
$$1,-1,1,-1,1,-1,\dots$$
Here $a_n=(-1)^{n-1}$ or $\{(-1)^{n-1}\},$ for $n=1,2\dots$



**Limits of Sequences:**
A sequence $\{a_n\}$ has the limit $L$ if $a_n$ approaches $L$ as $n$ approaches infinity. We write:
$$ \lim_{n\to\infty}a_n=L\space\text{or}\space a_n\to L \space \text{as} \space n\to \infty$$
If the limit exists we say that the sequence **converges**. 
Otherwise, we say the sequence **diverges**

##### Example
$a_n=\cfrac{1}{n}$ converges to 0
##### Example 2
$a_n=(-1)^{n-1}$ oscillates, does not converge to a finite value as $n\to \infty$, so it diverges.
##### Example 3
$a_n=n$ diverges to infinity.

The idea of the limit of sequences $\{a_n\}$ as $n\to\infty$ and the limit of a function $f(x)$ as $x\to\infty$ is essentially the same.

The only difference is that $n$ is an integer whereas $x$ is any real number.

Importantly, if $\lim_{n\to\infty}=L$ and $f(n)=a_n$ where $n$ is an integer, then:
$$\lim_{n\to\infty}a_n=L$$
This means that we can use our previous techniques for evaluating limits of functions to evaluate limits of sequences.