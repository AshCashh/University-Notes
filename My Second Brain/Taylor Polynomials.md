#math
Topics Covered:
Taylor polynomials
Taylor series, convergence 

## Taylor Polynomials
Often a reasonable approximation to a smooth function $f(x)$ near $x=x_0$ is:
$$P_1(x)=f(x_0)+f'(x_0)(x-x_0)$$
This is the equation to tangent line.

A better approximation near $x=x_0$ could be found by including a quadratic term:
$$P_2(x)=f(x_0)+f'(x_0)(x-x_0)+c_2(x-x_0)^2$$
If we force $f''(x_0)=P_1''(x_0),$ then $c_2=f''(x_0)/2,$ so:
$$P_2(x)=f(x_0)+f'(x_0)(x-x_0)+\cfrac{1}{2}f''(x_0)(x-x_0)^2$$
This line of thinking can continue, by matching higher order derivates to give the $n$th-order Taylor polynomial
$$P_n(x)=f(x_0)+f'(x_0)(x-x_0)+\cfrac{1}{2}f''(x_0)(x-x_0)^2$$
$$+\cfrac{1}{6}f'''(x_0)(x-x_0)+\dots+\cfrac{1}{n!}f^{(n)}(x_0)(x-x_0)^n$$
Or, using sigma notation, the approximation is:
$$f(x)\approx P_n(x)=\sum_{k=0}^n\cfrac{f^{(k)}(x_0)}{k!}(x-x_0)^k$$ 
### Example
Determine the 4th-order Taylor polynomial about $x=0$ for $f(x)=e^x$

Compute derivates:
$$f(x)=e^x,\space f'(x)=e^x,\space \dots, \space f''''(x)=e^x$$
Substitute in $x=0$:
$$f(0)=1,\space f'(0)=1,\space \dots, \space f''''(0)=1$$
Use formula:
$$\begin{align}
P_4(x)&=\sum_{k=0}^n\cfrac{f^{(k)}(x_0)}{k!}(x-x_0)^k\\
&=f(0)+f'(0)(x-0)+\cfrac{f''(0)}{2!}(x-0)^2+\cfrac{f'''(0)}{3!}(x-0)^3+\cfrac{f''''(0)}{4!}(x-0)^4\\
&=1+x+\cfrac{1}{2}x^2+\cfrac{1}{6}x^3+\cfrac{1}{24}x^4 \\
\end{align}
$$

### Example 2
Determine the 4th-order Taylor polynomial about $x=1$ for $f(x)=ln(x)$

Compute derivates:
$$f(x)=ln(x),\space f'(x)=\cfrac{1}{x},\space f''(x)=-\cfrac{1}{x^2},\space f'''(x)=\cfrac{2}{x^3},f''''(x)=-\cfrac{6}{x^4}$$
Sub $x=1$:
$$f(1)=0,\space f'(1)=1,\space f''(1)=-1,\space f'''(1)=2,\space f''''(1)=-6$$
Use formula:
$$
\begin{align}
P_4(x)&=\sum_{k=0}^n\cfrac{f^{(k)}(x_0)}{k!}(x-x_0)^k \\
&=f(x_0)+f'(x_0)(x-x_0)+\cfrac{f''(x_0)}{2!}(x-x_0)^2+\cfrac{f'''(x_0)}{3!}(x-x_0)^3+\cfrac{f''''(x_0)}{4!}(x-x_0)^4 \\
&=0+x-1-\cfrac{1}{2!}(x-1)^2+\cfrac{2}{3!}(x-1)^3-\cfrac{6}{4!}(x-1)^4 \\
&=x-1-\cfrac{1}{2}(x-1)^2+\cfrac{1}{3}(x-1)^3-\cfrac{1}{4}(x-1)^4 \\ 

\end{align}
$$

### Example 3
Recall the 4th-order Taylor polynomial about $x=1$ for $f(x)=ln(x)$ in Example 2:
$$P_4(x)=x-1-\cfrac{1}{2}(x-1)^2$+\cfrac{1}{3}(x-1)^3-\cfrac{1}{4}(x-1)^4 $$
It turns out that $P_4$ is a reasonable approximation for $ln(1/2)$:
$$P_4(1/2)=-\cfrac{1}{2}-\cfrac{1}{2(-2)^2}+\cfrac{1}{3(-2)^3}-\cfrac{1}{4(-2)^4}=\cfrac{131}{192}=-0.68229\dots,$$
compared to the exact value:
$$ln(1/2)=-0.69314\dots$$
But interesting, we get a very different result if we sub in $x=3$:
$$P_4(3)=2-\cfrac{2^2}{2}+\cfrac{2^3}{3}-\cfrac{2^4}{4}=-\cfrac{4}{3},$$
but 
$$ln(3)=1.09861\dots$$
That is, $P_4(3)$ is not a reasonable approximation for $ln(3)$ at all.

# Taylor Series 
We extend Taylor polynomials to Taylor series by taking the limit $n\to\infty$.

Provided the function $f(x)$ has derivates of all orders at the point $x=x_0$, the Taylor series for $f$ about $x=x_0$ is defined to be:
$$
\begin{align}
\sum_{k=0}^{\infty}\cfrac{f^{(k)}(x_0)}{k!}(x-x_0)^k&=f(x_0)+f'(x_0)(x-x_0)+\cfrac{1}{2}f''(x_0)(x-x_0)^2 \\
&+\dots+\cfrac{1}{n!}f^{(n)}(x_0)(x-x_0)^{n}+\dots \\
\end{align} $$
If $x_0=0$, then some call this a Maclaurin series.

## Convergence of Taylor Series
A full Taylor series, which is found by taking the limit of an $n$th-order Taylor polynomial as $n\to\infty$, has a radius of convergence $R$, which can be found using the ratio rest:
$$\begin{align}
&(1)\space\text{If $R=0$, the series converges at}\space x=x_0\space\text{(we say the series has a zero radius of convergence)} \\
\\
&(2)\space\text{If $R>0$, is some finite number, then the series converges on the interval:} \\
&\quad\space\space\space\text{$x_0-R<x<x_0+R$ and diverges outside the interval} \\
\\ 
&(3)\space \text{The convergence at the end points $x=x_0-R$ and $x=x_0+R$ needs checking as the series may converge or diverge.} \\
\\
&(4)\space \text{If the radius of convergence is infinite, the series converges for all $x$} \\
\end{align}
$$
### Example
Determine the interval of convergence of the Maclaurin series for $f(x)=e^x$. 

For this (relatively simple) example, we have already worked (in [[Taylor Polynomials#Example|Example]]) out that:
$$f^{(k)}(0)=1,\qquad \text{for all}\quad k\leq0$$
Therefore, the Taylor series for $e^x$ about $x=0$ is:
$$\sum_{k=0}^{\infty}\cfrac{f^{(k)}(0)}{k!}x^k=\sum_{k=0}^{\infty}\cfrac{x^k}{k!}$$
Apply ratio test:
$$\rho=\lim_{k\to\infty}\left|\cfrac{a_{k+1}}{a_k}\right|=\lim_{k\to\infty}\left|\cfrac{x^{k+1}/(k+1)!}{x^k/k!}\right|$$
$$=\lim_{k\to\infty}\left|\cfrac{xk!}{(k+1)!}\right|=\lim_{k\to\infty}\left|\cfrac{x}{k+1}\right|=0\quad \text{for all $x$}$$
Since $\rho<1$ for all $x$, Taylor series converges for all $x$, i.e. $R=\infty$; interval of convergence: $-\infty<x<\infty$.

### Example 2
Determine the interval of convergence of the Taylor series for $f(x)=ln(x)$ about $x=1$.

From [[Taylor Polynomials#Example 2|Example2]], we worked out that:
$$f^{(k)}(1)=(-1)^{k-1}(k-1)!, \qquad\text{for all}\quad k\geq 1$$
Therefore, the Taylor series for $ln(x)$ about $x=1$ is:
$$\sum_{k=1}^{\infty}\cfrac{f^{(k)}(1)}{k!}(x-1)^k=\sum_{k=1}^{\infty}\cfrac{(-1)^{k-1}(k-1)!(x-1)^k}{k!}
$$
$$=\sum_{k=1}^{\infty}\cfrac{(-1)^{k-1}}{k}(x-1)^k
$$
Apply ratio test:
where $a_k$ is $\cfrac{(-1)^{k-1}}{k}(x-1)^k$, note: absolute value of the limit cancel out $(-1)^{k-1}$
$$\rho=\lim_{k\to\infty}\left|\cfrac{a_{k+1}}{a_k}\right|=\lim_{k\to\infty}\left|\cfrac{(x-1)^{k+1}/(k+1)}{(x-1)^{k}/k)}\right|$$
$$=\lim_{k\to\infty}\left|\cfrac{(x-1)k}{k+1}\right|=|x-1|\lim_{k\to\infty}\left|\cfrac{k}{k+1}\right|
=|x-1|$$
Converges if $\rho<1,$ i.e. $|x-1|<1$, $0<x<2$.

Must check the end points:
$x=0$:
$$\sum_{k=1}^{\infty}\cfrac{(-1)^{k-1}(-1)^k}{k}=-\sum_{k=1}^{\infty}\cfrac{1}{k}$$
Which is a harmonic series that diverges.
$x=2$:
$$\sum_{k=1}^{\infty}\cfrac{(-1)^{k-1}}{k}$$
Which is an alternating series that converges.

Therefore, the interval of convergence of the original Taylor series is $0<x\leq 2$ and $R = 1$.

## Manipulating Taylor Series
We can integrate or differentiate series term by term and the radius of convergence does not change (although the end points will need checking for convergence).

We can also make substitutions, if we are careful.

For example, we have:
$$e^x=\sum_{k=1}^{\infty}\cfrac{x^k}{k!}=1+x+\cfrac{1}{2}x^2+\cfrac{1}{6}x^3+\dots,$$
for all $x$, so if we wanted to find $e^{x^2}$, we can replace $x$ with $x^2$ using substitution :
$$e^{x^2}=1+x^2+\cfrac{1}{2}x^4+\cfrac{1}{6}x^6+\dots$$
### Example
Determine the Taylor series for $f(x)=\frac{1}{x}$ about $x=1$, together with the interval of convergence. 

We know that:
$$ln(x)=\sum_{k=1}^{\infty}\cfrac{(-1)^{k-1}(x-1)^k}{k}=x-1-\cfrac{1}{2}(x-1)^2+\cfrac{1}{3}(x-1)^3-\cfrac{1}{4}(x-1)^4+\dots,$$
provided $0<x\leq 2$.

Then differentiate each term, so that:
$$\cfrac{1}{x}=1-(x-1)+(x-1)^2-(x-1)^3+\dots$$
To check the interval of convergence, $R=1$ remains the same but we must check the end points.

$x=0$:
$$1+1+1+\dots\quad\text{diverges}$$
$x=2$:
$$1-1+1-\dots\quad\text{diverges}$$
Therefore it converges from $0<x<2$.

## Summary
- There are all sorts of issues about proving convergence of power series that are interesting but not important for us
- What's important for us is to image that a Taylor polynomial may be thought of as an approximation to a function. If the limit that we take infinitely many terms, the Taylor series may actually equal the function. if we are close enough to the point $x=x_0$ (within the distance $R$, the radius of convergence).
- You need to be able to calculate a Taylor polynomial to a given order.
- For a full Taylor series, you need to be able to calculate the interval of convergence, including the end points
