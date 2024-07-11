---
tags: [math, logic]
Created: 2023-07-30T09:53:45+10:00
Modified: 2024-07-03T19:35:33+10:00
---
# [[Mathematics|Mathematical]] Functions 

## Periodic Function
A function $f(t)$ is periodic if there is a positive number $T$ such that
$$f(t)=f(t+T)\qquad \text{for all $t$}$$
Here $T$ is called the period of $f(t)$ 

The graph of $f(t)$ is obtained by periodic repetition of its graph in any interval of length $T$. Important examples of periodic functions are [[Trigonometric Functions]]

# Even and Odd Functions
## Even Functions
A function $x(t)$ is even if:
$$x(-t)=x(t)$$
for all t in the functions domain. Even functions are symmetric about the vertical axis.

## Odd Functions
A function $x(t)$ is odd if:
$$x(-t)=-x(t)$$
Or
$$
x(t)=-x(-t)
$$
for all t in the functions domain. Odd functions are symmetric about the origin.

### Integrating Even and Odd Functions
When integrating an even function $x(t)$ over the domain $[-T,T]$:
$$\int_{-T}^{T}x(t)\space dt=2\int_0^{T}x(t)\space dt.$$
Similarly, when integrating an odd function $x(t)$ over the domain $[-T,T]$:
$$\int_{-T}^{T}x(t)\space dt =0$$
### Product of Even and Odd Functions
1. The product of an even function with an even function, is an even function.
$$
\begin{align}
\text{Let $f(t)$ and $g(t)$ be eve}&\text{n functions, and let $h(t)=f(t)g(t)$,} \\
&h(-t)=f(-t)g(-t)=f(t)g(t)=h(t).\\
\end{align}
$$
2. The product of an even function with odd function, is an odd function.
$$
\begin{align}
\text{Let $f(t)$ be eve}&\text{n function and $g(t)$ be an odd function, and let $h(t)=f(t)g(t)$}, \\
&h(-t)=f(-t)g(-t)=(-f(t))g(t)=-h(t) \\
\end{align}
$$
3. The product of an odd function with an odd function, is an even function.
$$
\begin{align}
\text{Let $f(t)$ and $g(t)$ be odd}&\text{ functions, and let $h(t)=f(t)g(t)$}, \\
&h(-t)=f(-t)g(-t)=(-f(t))(-g(t))=f(t)g(t)=h(t).\\
\end{align}
$$

## [[Fourier Series]] for Even Functions
Suppose $f(t) =\displaystyle cos\left(\frac{2\pi nt}{T}\right)$, which is an even function:
So $f(t)$ may be represented by a Fourier cosine series:
$$\begin{align}
f(t)&=a_0+\sum_{n=1}^{\infty}a_n\space cos\left(\frac{2\pi nt}{T}\right) \\
\text{where}\qquad a_0&=\frac{2}{T}\int_{0}^{T/2}f(t)\space dt \\ 
\\
a_n&=\frac{4}{T}\int_0^{T/2}f(t)\space cos\left(\frac{2\pi nt}{T}\right) dt \\
\\
b_n&=0
\end{align}
$$
## [[Fourier Series]] for Odd Functions
Suppose $f(t) =\displaystyle sin\left(\frac{2\pi nt}{T}\right)$, which is an odd function:
So $f(t)$ may be represented by a Fourier sine series:
$$
\begin{align}
f(t)&=\sum_{n=1}^{\infty}b_n\space sin\left(\frac{2\pi nt}{T}\right)\\
\text{where}\qquad b_n&=\frac{4}{T}\int_0^{T/2}f(t)sin\left(\frac{2\pi nt}{T}\right)\space dt \\
\\
a_0&=a_n=0


\end{align}
$$


# Orthogonality
An inner product generalises the dot product in general vector spaces.
In particular, for the function space $\mathscr{F}([a,b])$, where $t\in[a,b]$, the inner product is defined as the following:
$$
\langle f,g \rangle=\int_a^bf(t)\space g(t)\space dt
$$
for $f,g\in\mathscr{F}([a,b])$ 

Given an inner product space, two vectors are **orthogonal** if:
$$\langle f,g \rangle=0$$
We also say the norm of a function $f(t)$ is:
$$
||f(t)||=\left(\int_{a}^{b}f(t)^2\space dt\right)^{1/2}
$$
## Orthogonality of Trigonometric Functions
Consider the inner product between the sine and cosine functions on the interval $[-T,T]$ 
$$\langle sin(t),cos(t) \rangle=\int_{-T}^Tsin(t)\space cos(t)\space dt = 0$$
as the integrand is an odd function.

### Examples
For example if we set $T=2\pi$ for simplicity, then key results are:
$$\begin{align}
&\int_{-\pi}^{\pi}cos(At)\space cos(Bt)\space dt=\int_{-\pi}^{\pi}sin(At)\space sin(Bt)\space dt= 0,\qquad n\neq m \\

&\int_{-\pi}^{\pi}sin(At)\space cos(Bt)\space dt=0 \\
&\int_{-\pi}^{\pi}cos^2(At)\space dt=\int_{-\pi}^{\pi}sin^2(At)\space dt =\pi
\end{align}
$$

# Logical Functions
In [[Mathematical Logic|Logic]], a function is a relation $f$ between $A$ and $B$ where for each $a\in A$ there is exactly one $b\in B$ such that $(a,b)\in f$.
$$((a,b)\in f\land(a,c)\in f)\to b=c$$
We can write this as: 
$$f:A\to B$$
where, $f(a)$ is the unique $b\in B$ such that $(a,b)\in f$.

Usually it's said that a function $f:A\to B$ is defined on all of $A$ meaning:
$$\forall a\in A\exists !b\in B(a,b)\in f$$
The $!$ notation simply means unique. So in the above definition we're saying there exists a unique $b$ for every $a$.

## Domain and Range
For a function $f:A\to B$, we call $A$ the domain of $f$ (function) and $B$ the co-domain. The set $\{f(x):x\in A\}$ is called the range of $f$.

The domain is a set of every element for which $f$ is defined. This essentially means that the domain the set of possible inputs to $f$ while the range is the set of all possible outputs.

### Examples
For:
- $\{(1,\pi),(2,\beta),(3,\alpha),(4,\gamma)\}$ 
Domain: Set of all values getting mapped (1,2,3,4)
Co-domain: Some of the greek letters
Range: Set of values $\pi,\beta,\alpha,\gamma$

For:
- $\{(1,\pi),(2,\pi),(3,\pi),(4,\pi)\}$
Domain: (1,2,3,4)
Range: $\pi$

- $\{(a,b)\in\mathbb{R}^2:b=a^2\}$
- $=(S\to S\text{ for any } S)$
- $(x,y)$ co-ordinates for drawing a 45 degree line

Non-math functions:
- $f(x)$ given by the last name of the QUT student with student number x
- $f(x)$ given the URL for the first response for a google search on x
- $f(x)$ given by the MD5 hash of the bit string

Non-function:
- $\{(1,\pi),(1,\gamma)\}$ (not unique 1)
- $\{(a,b)\in \mathbb{R}^2:a=b^2\}$ (some values of a are not unique or don't exist)
- $(x,y)$ co-ordinates for drawing a happy face

## Composing Functions
Let's imagine we have two functions: $f:A\to B$ and $g:B\to C$. Instead of first running $f$ then $g$ we can combine the two using $\textopenbullet$ (of) notation. For example:
$$g\textopenbullet f:A\to C$$
The above definition is given by:
$$(g\textopenbullet f)(x)=g(f(x))$$
Or more formally:
$$g\textopenbullet f=\{(x,z)\in A\times C:\exists y\in B(x,y)\in f\land(y,z)\in g\}$$
## Inverse Functions
Some functions, not all have an inverse property. Given by: $f:A\to B$, there may exist an inverse $f^{-1}:B\to A$ such that:
$$\forall x \in A(f^{-1}\textopenbullet f(x)=x)$$
It's important to note that the range of $f$ must match the domain of $f^{-1}$.

### Example
$$\begin{align}
f&=\{(1,a),(2,b),(3,c)\}\\
A=\{1,2,3\}&\space\space\space B=\{a,b,c\}\\
f^{-1}&=\{(b,2),(a,1),(c,3)\}\\
f^{-1}\textopenbullet f(1)&=f^{-1}(a)=1
\end{align}
$$