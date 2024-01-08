#math
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

# [[Fourier Series]] for Even Functions
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
# [[Fourier Series]] for Odd Functions
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


```


```