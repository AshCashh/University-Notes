---
tags: [math]
Created: 2023-09-14T11:31:01+10:00
Modified: 2024-07-03T19:35:33+10:00
---
[[Mathematics]]
# Line Integrals in 2D
Remember the definite integrals:
$$\int_a^bg(x)\space dx$$
has the interpretation of an area between $z=g(x)$ and $x$-axis.
$$\int_c^dh(y)\space dy$$
has the interpretation of an area between $z=h(y)$ and $y$-axis.

A line integral $\displaystyle\int_Cf(x,y)\space ds$ generalises these ideas to an area between $z=f(x,y)$ and a curve $C$ in the $xy$-plane. 
Such that:
$$\begin{align*}
\int_Cf(x,y)\space ds=\int_a^bf(x(t),y(t))\sqrt{x'(t)^2+y'(t)^2}\space dt\\
\int_Cf(x,y)\space \frac{ds}{dt}dt=\int_a^bf(x(t),y(t))\sqrt{x'(t)^2+y'(t)^2}\space dt
\end{align*}$$
## Parameterisation of Curves in 2D
A curve $C$ in $\mathbb{R}^2$ is given by a set of points:
$$(x(t),y(t))$$
Considering $x$ and $y$ as functions of $t$ denotes a parameterisation of the curve. 
The parameterisation defines an orientation on $C$ in the direction of increasing $t$. 
We can write the curve $C$ as a vector function:
$$\mathbf{r}(t)=x(t)\mathbf{i} + y(t)\mathbf{j}$$
with endpoints at $\mathbf{r}_0=\mathbf{r}(a)$ and $\mathbf{r}_1=\mathbf{r}(b)$.
![[Pasted image 20230914125050.png|centre|300]]
### Straight Lines
$$\mathbf{r}(t)=\mathbf{r}_0+t(\mathbf{r}_1-\mathbf{r}_0)$$
$$0<t<1$$

## Parameterisation of Curves in 3D
A curve $C$ in $\mathbb{R}^3$ is given by a set of points:
$$(x(t),y(t),z(t))$$
Where the curve $C$ can be written as a vector function:
$$\mathbf{r}(t)=x(t)\mathbf{i}+y(t)\mathbf{j}+z(t)\mathbf{k}$$
with endpoints at $\mathbf{r}_0=\mathbf{r}(a)$ and $\mathbf{r}_1=\mathbf{r}(b)$.

```tikz 
\begin{document} 
\begin{tikzpicture}[domain=0:10] 
\draw[->] (0,0,0) -- (3,0,0)node[below]{$x$};
\draw[->] (0,0,0) -- (0,3,0)node[below]{$y$};
\draw[->] (0,0,0) -- (0,0,3)node[left]{$z$};
\draw [fill] (0,0,0) circle (0.5pt) node[below]{0};
\draw[thick] (0,0,1) to[out=80,in=165] (1,1,2) coordinate(X) to[out=-15,in=150] (1,2.5,1);
\draw[->] (0,0,0) -- (X) node[midway,right]{$\vec r$};
\draw[->] (X) --++(0.1,0.4,0.) node[above] {d$\vec r$}; 
\end{tikzpicture} 
\end{document} 
```

### Example 1
The parabola $y=x^2$ from the point $\mathbf{r}_0=(a,a^2)$ to $\mathbf{r}_1=(b,b^2)$.
A parameterisation is:
$$
\left.
\begin{array}{l}
x(t)=t\\
y(t)=t^{2}&
\end{array}
\right\}
\text{ for }a\leq t\leq b
$$
### Example 2
The circle $x^2+y^2=a^2$, oriented anticlockwise.
A parameterisation is:
$$
\left.
\begin{array}{l}
x(t)=a\cos(t)\\
y(t)=a\sin(t)&
\end{array}
\right\}
\text{ for }0\leq t\leq 2\pi
$$
Note that a circle is a closed curve (it begins and starts at the same point).

If the circle were oriented clockwise, starting at $(a,0)$ we could use:
$$
\left.
\begin{array}{l}
x(t)=a\cos(t)\\
y(t)=-a\sin(t)&
\end{array}
\right\}
\text{ for }0\leq t\leq 2\pi
$$
### Example 3
The ellipse $\cfrac{x^2}{a^2}+\cfrac{y^2}{b^2}=1$, oriented anticlockwise:
A parameterisation is:
$$
\left.
\begin{array}{l}
x(t)=a\cos(t)\\
y(t)=b\sin(t)&
\end{array}
\right\}
\text{ for }0\leq t\leq 2\pi
$$
### Example 4
The straight line from the point $\mathbf{r}_0=(x_0,y_0,z_0)$ to the point $\mathbf{r}_1=(x_1,y_1,z_1)$.
A parameterisation is:
$$
\begin{align*}
x(t)&=x_0+t(x_1-x_0)\\
y(t)&=y_0+t(y_1-y_0)\\
z(t)&=z_0+t(z_1-z_0)
\end{align*}
$$
where $0\leq t\leq 1$.

# Line Integrals in 3D
Let $C$ be a curve with parameterisation
$$\mathbf{r}(t)=x(t)\mathbf{i} + y(t)\mathbf{j} + z(t) \mathbf{k}$$
and endpoints at $\mathbf{r}_0=\mathbf{r}(a)$ and $\mathbf{r}_1=\mathbf{r}(b)$.

We define the line integral of $f$ along $C$ to be:
$$\int_Cf(x,y,z)\space ds $$
where $s$ denotes arc length. It is equal to:
$$\int_a^b f(x,y,z)\frac{ds}{dt}\space dt=\int_a^bf(x(t),y(t),z(t))\sqrt{x'(t)^2+y'(t)^2+z'(t)^2}\space dt$$
where $\displaystyle x'(t)^{2}= \left(\frac{dx}{dt}\right)^2,y'(t)^{2}= \left(\frac{dy}{dt}\right)^2, z'(t)^{2}= \left(\frac{dz}{dt}\right)^2$ 
### Example 1
The arc length of the curve $C$ is given by 
$$\begin{align*}
\text{Length}&=\int_C\space ds\\
&=\int_a^b \sqrt{x'(t)^2+y'(t)^2+z'(t)^2} \space dt
\end{align*}$$
If $\rho$ is the linear charge density at any point $(x,y,a)$ on a piece of wire bent into the shape of the curve $C$, then the total charge along the wire is given by:
$$\text{Charge}=\int_C\rho(x,y,z)\space ds$$
Consider the helix with parameterisation
$$\mathbf{r}(t)=\cos t \mathbf{i}+sin t \mathbf{j} + 2t \mathbf{k}$$
Let $C$ be the coil from $(1,0,0)$ to $(1,0,4\pi)$.
If the linear charge density along the coil is:
$$\rho = x^2+2z$$
calculate the length and total charge of the coil.

At $(1,0,0)$, $t=0$.
At $(1,0,4\pi)$, $t=2\pi$. 
Therefore, the integral goes from $0\leq t\leq 2\pi$:
$$\begin{align*}
\text{Length}&=\int_a^b \sqrt{x'(t)^2+y'(t)^2+z'(t)^2} \space dt\\
&=\int_a^b\sqrt{(-\sin t)^{2+(\cos t)^{2}+2^{2}}\space}dt\\
&=\int_a^b\sqrt{5}\space dt=2\sqrt{5}\pi\\
\text{Charge}&=\int_C\rho(x,y,z)\space ds\\
&=\int_Cx^2+2z\space ds\\
&=\int_0^{2\pi}[\cos^2t+4t]\sqrt{5}\space dt\\
&=\sqrt{5}\int_0^{2\pi} \frac{1}{2}(1+\cos(2t))+4t\space dt\\
&=\sqrt{5} \left[\frac{t}{2}+ \frac{sin(2t)}{4}+2t^2\right]_0^{2\pi}\\
&=\sqrt{5}(\pi+8\pi^2)
\end{align*}$$


# Closed Curves
If $C$ is a closed curve, then for a line integral along $C$, we use the notation:
$$\oint_Cf(x,y,z)\space ds$$
In this case the end points $\mathbf{r}_0$ and $\mathbf{r}_1$ coincide. 