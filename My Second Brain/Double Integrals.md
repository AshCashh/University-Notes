---
tags: [math]
Created: 2023-08-31T18:45:23+10:00
Modified: 2024-07-03T19:35:33+10:00
---
[[Mathematics]]
Let $S$ be a surface given by the equation:
$$z=f(x,y)$$
and let $R$ be a region in the $xy$-plane.
![[Pasted image 20230831184624.png|centre|300]]
Let $\Delta A_i=\Delta x_i \Delta y_i$ represent a small subregion of $R$. The double integral of $f$ over $R$ is:
$$\begin{align}
\int\int_Rf\space(x,y)\space dA &=\lim_{n\to\infty}\sum_{i=1}^n\space f(x_i,y_i)\Delta A_i \\
&=\int\int_R\space f(x,y)\space dx\space dy
\end{align}$$
## Volume Under the Surface
The volume between the $xy$-plane and the surface $z=f(x,y)$ over the region $R$ is:
$$\text{Volume under } f(x,y)=\int\int_Rf(x,y)\space dx\space dy$$
## Area of a Region 
The area of region $R$ in the $xy$-plane corresponds to the case in which $f(x,y)=1$: 
$$\text{Area of } R=\int\int_R\space dx\space dy$$
# Double Integral over general regions
### Vertical Strips
A region can be described by vertical strips if:
$$\begin{align}
g(x)\leq\space &y \leq h(x) \\
a\leq \space&x\leq b
\end{align}$$
for some functions $g(x)$ and $h(x)$. 
![[Pasted image 20230831200624.png|centre|300]]
$$\int_{a}^{b}\int_{g(x)}^{h(x)}\space f(x,y)\space dy\space dx$$
In this case we integrate with respect to $y$ first (the inner region).
### Horizontal Strips
A region can be described by vertical strips if:
$$\begin{align}
g(y)\leq\space &x \leq h(y) \\
c\leq \space&y\leq d
\end{align}$$
for some functions $g(x)$ and $h(x)$. 
![[Pasted image 20230831201141.png|centre|300]]
$$\int_c^d\int^{h(y)}_{g(y)} \space f(x,y)\space dx\space dy$$
In this case we integrate with respect to $x$ first.

# Example
Evaluate:
$$\int\int_Rxy^2\space dA$$
where $R$ is the region bounded by the lines $y=0$, $y=x^2$ and $x=1$.
The region $R$ can be described using vertical or horizontal strips:

### Vertical Strips (inner y):
![[Pasted image 20230831201740.png|200]]
For vertical strips:
$$\int_0^1\int_0^{x^2}\space xy^2\space dy\space dx$$
### Horizontal Strips (inner x):
For horizontal strips:
$$\int_0^{1}\int_{\sqrt{y}}^1 \space xy^2\space dx\space dy$$

