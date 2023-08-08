#math
# [[Mathematics|Mathematical]] Functions 

## Periodic Function
A function $f(t)$ is periodic if there is a positive number $T$ such that
$$f(t)=f(t+T)\qquad \text{for all $t$}$$
Here $T$ is called the period of $f(t)$ 

The graph of $f(t)$ is obtained by periodic repetition of its graph in any interval of length $T$. Important examples of periodic functions are [[Trigonometric Functions]]

## Even and Odd Functions
A function $x(t)$ is even if:
$$x(-t)=x(t)$$
for all t in the functions domain. Even functions are symmetric about the vertical axis.

A function $x(t)$ is odd if:
$$x(-t)=-x(t)$$
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
