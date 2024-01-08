#math
Let $S$ be a smooth surface defined by the function $z=f(x,y)$.
Let $g(x,y,z)$ be a function that is continuous on $S$.

One definition of a surface integral of $g$ over $S$ is:
$$\int\int_Sg(x,y,z)\space dS=\int\int_Rg(x,y,f(x,y)) \sqrt{f_x^2+f_y^2+1}\space dy\space dx$$
where $R$ is the region formed by projecting $S$ onto the $xy$-plane.

For one interpretation, sketch a surface of height $g$ above $S$ to form a "house" whose "floor" is the surface $S$ and whose "roof" has height $g$. The surface integral: $\displaystyle\int\int_Sg(x,y,z)\space dS$ represents the volume of the "house".

### Example
The surface area of $S$ corresponds to the case where $g=1$:
$$\text{Area}=\int\int_S\space dS=\int\int_R \sqrt{f_x^2+f_y^2+1}\space dy\space dx$$
If $\rho$ is the surface charge density at any point $(x,y,z)$ on a sheet of metal bent into the shape of the surface $S$, then the total charge of the sheet is given by:
$$\begin{align*}
\text{Charge}&=\int\int_S\rho(x,y,z)\space dS\\
&=\int\int_R\rho(x,y,f(x,y,z))\sqrt{f_x^2+f_y^2+1}\space dy\space dx
\end{align*}$$
#### Cone Example
Let $S$ be the portion of the cone $z=\sqrt{x^2+y^2}$ that lies between the planes $z=1$ and $z=2$. Assume the surface charge density at any point $(x,y,z)$ on this truncated cone is given by $\rho=x^2y^2z$.
![[Pasted image 20230914182310.png|centre|00]]
Find the:
**a)** Surface area of the truncated cone.
$$\begin{align*}
\text{Surface Area}&=\int\int_S1\space dS\\
&=\int\int_R \sqrt{f_x^2+f_y^2+1}\space dx\space dy\\

\end{align*}$$
$$f_x=\frac{1}{2}\cdot2x(x^2y^2)^{-\frac{1}{2}}=\frac{x}{\sqrt{x^2+y^2}}$$
$$f_y=\frac{1}{2}\cdot2y(x^2y^2)^{-\frac{1}{2}}=\frac{y}{\sqrt{x^2+y^2}}$$
$$f_x^2f_y^2=\frac{x^2y^2}{x^2y^2}=1$$
$$\therefore\text{Surface Area}=\int\int_R\sqrt{2}\space dy\space dx$$
Using polar coordinates:
$$x=r\cos\theta, \quad y=r\sin\theta,\quad dy\space dx=rdr\space d\theta$$
$$\begin{align*}
1\leq \space &r\leq 2 \\
0\leq\space&\theta\leq2\pi
\end{align*}$$
$$\text{Surface Area}=\sqrt{2}\int_0^{2\pi}\int_1^2r\space dr\space d\theta\space =3\sqrt{2}\pi
$$
**b)** Total charge of the truncated cone.
$$\begin{align*}
\text{Charge}&=\int\int_S\rho(x,y,z)\space dS\\
&=\int\int_R\rho(x,y,f(x,y)) \sqrt{f_x^2+f_y^2+1}\space dx\space dy\\
&=\int\int_R x^2y^2\sqrt{x^2+y^2}\sqrt{2}\space dy\space dx
\end{align*}$$
Using polar coordinates as above:
$$\begin{align*}
\text{Charge}&=\sqrt{2}\int_0^{2\pi}\int^2_1r^2\cos^2\theta r^2\sin^2\theta r^2\space dr\space d\theta\\
&=\sqrt{2}\int_0^{2\pi}\int_1^2r^6(\cos\theta\sin\theta)^2\space dr\space d\theta \\
&=\sqrt{2}\int_0^{2\pi} \left[\frac{r^7}{7}\right]_1^2 \frac{sin^22\theta}{4}\space d\theta\\
&= \frac{\sqrt{2}}{28}(2^7-1)\int_0^{2\pi}\frac{1-\cos4\theta}{2}\space d\theta\\
&=\frac{\sqrt{2}}{28}(2^7-1) \left[\frac{\theta}{2}-\frac{\sin4\theta}{8}\right]_0^{2\pi}\\
&=\frac{\sqrt{2}\pi}{28}(2^7-1)
\end{align*}$$
# Flux Integral
## Flux Across A Surface
Let $S$ be a smooth oriented surface defined by the equation $z=f(x,y)$. Assume the orientation of $S$ is such that the unit normal vector $\mathbf{\hat{n}}$ on $S$ is upward. Let:
$$\mathbf{F}=F_1\mathbf{i}+F_2\mathbf{j} + F_3\mathbf{k}$$
be a [[Vector Fields|Vector Field]] that is continuous on $S$. 
One way to define a surface integral of $\mathbf{F}$ over $S$ is:
$$\int\int_S \mathbf{F}\cdot \mathbf{\hat{n}}\space dS=\int\int_R-F_1f_x-F_2f_y+F_3\space dy\space dx$$
where $R$ is the region formed by projecting $S$ onto the $xy$-plane.

If it's downwards, add a negative.
## Interpretation
For one interpretation, if $\mathbf{F}$ is the velocity field of a moving fluid, then
$$\int\int_S \mathbf{F}\cdot \mathbf{\hat{n}}\space dS=\oint_C \mathbf{F} \cdot d \mathbf{r}$$
gives the flux of $\mathbf{F}$ across $S$, which is the net volume of fluid, per unit time, flowing across $S$ in the direction $\mathbf{\hat{n}}$.

### Flux Example
Let $S$ be the part of the plane:
$$2x-2y+z=6$$
that lies above the triangle in the $xy$-plane that is bounded by the lines $y=0,x=1$ and $y=2x$. Assume $S$ is oriented with its unit normal $\mathbf{\hat{n}}$ upwards.

Find the flux of the vector field $\mathbf{F}=x \mathbf{i}+y \mathbf{j}+2\mathbf{k}$ across $S$.

$S$ is defined by:
$$z=f(x,y)=6-2x+2y$$
so
$$f_x=-2\quad f_y=2$$
Projecting $S$ onto the $xy$-plane gives the region $R$:
Using vertical strips, $R$ can be described as:
$$\begin{align*}
0\leq\space &y\leq2x\\
0\leq\space &x\leq 1
\end{align*}$$
The components of $\mathbf{F}$ are:
$$F_1=x,\space F_2=y,\space F_3=2$$
As $\mathbf{n}$ is upwards, the flux across $S$ is:
$$\begin{align*}
\int\int_S \mathbf{F}\cdot \mathbf{\hat{n}}\space dS&=\int\int_R-F_1f_x-F_2f_y+F_3\space dy\space dx\\
&=\int_0^1\int_0^{2x}2x-2y+2\space dy\space dx\\
&=\int_0^1[2xy-y^2+2y]_0^{2x}\space dx\\
&=\int_0^14x\space dx\\
&=[2x^2]_0^1\\
&=2
\end{align*}$$