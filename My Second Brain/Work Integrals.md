---
tags: [math]
Created: 2023-09-14T16:14:45+10:00
Modified: 2024-07-03T19:24:55+10:00
---
[[Mathematics]]
Let $C$ be a curve with parameterisation $\mathbf{r}(t)=x(t)\mathbf{i}+y(t)\mathbf{j}+ z(t)\mathbf{k}$ with endpoints at $\mathbf{r}_0=\mathbf{r}(a)$ and $\mathbf{r}_\mathbf{r}(b)$.
Let $\mathbf{F}=F_1\mathbf{i}+F_2\mathbf{j}+F_3\mathbf{k}$ be a [[Scalar Fields|Scalar Field]].

We define the line integral (work integral) of $\mathbf{F}$ along $C$ to be:
$$\int_C \mathbf{F}\cdot\space d \mathbf{r}$$
where 
$$d \mathbf{r}= \frac{d \mathbf{r}}{dt}=x'(t)\mathbf{i}+y'(t) \mathbf{j}$$
The work done by a force $\mathbf{F}$ in moving a particle along $C$ from $\mathbf{r}_0$ to $\mathbf{r}_1$ is given by:
$$\begin{align*}
\text{Work}&=\int_C \mathbf{F}\cdot \space d \mathbf{r}\\
&=\int_a^b \mathbf{F}[\mathbf{r}(t)]\cdot \mathbf{r}'(t)\space dt \\
&=\int_a^b F_1x'(t)+F_2y'(t)+F_3z'(t)\space dt\\
&=\int_C F_1dx+F_2dy+F_3fz\space \text{(differential form)}
\end{align*}$$
## Example
A particular moves along the helix $C$ parameterised by:
$$\mathbf{r}(t)=\cos t \mathbf{i}+\sin t \mathbf{j}+t \mathbf{k}$$
from $\mathbf{r}_0=(1,0,0)$ to $\mathbf{r}_1=(1,0,2\pi)$.
If the applied force is:
$$\mathbf{F}=-zy \mathbf{i}+zx \mathbf{j}+ xy \mathbf{k}$$
find the work done by the force.
$$\begin{align*}
\text{Work}&=\int_C \mathbf{F}\cdot \space d \mathbf{r}\\
&=\int_0^{2\pi} \mathbf{F} \cdot\frac{d \mathbf{r}}{dt}\space dt \\
\end{align*}$$
Calculate $\mathbf{r}'(t)=-\sin t \mathbf{i}+\cos t \mathbf{j}+\mathbf{k}$:
Calculate $\mathbf{F}=-t\sin t \mathbf{i}+t\cos t \mathbf{j}+\sin t\cos t \mathbf{k}$
$$\begin{align*}
\therefore &=\int_0^{2\pi} [t \sin^2t+t\cos^2t+\sin t\cos t] \space dt\\
&=\int_0^{2\pi}t+ \frac{1}{2}\sin 2t \space dt\\
& = \left[\frac{1}{2}t^2 - \frac{1}{4}\cos 2t\right]_0^{2\pi}=2\pi^2

\end{align*}$$
# Path Dependence
In general, the line integral $\int_C \mathbf{F}\cdot \space d \mathbf{r}$ depends crucially on the path $C$, not just the end points $a$ and $b$.

However, in the special case where we can write $\mathbf{F}=\nabla\phi$ for some $\phi$, then the path does not matter.

In that case, we have:
$$\int_C \mathbf{F}\cdot \space d \mathbf{r}\space d \mathbf{r}=\int_C \nabla\phi \cdot \space d \mathbf{r}=\phi(b)-\phi(a)$$
Important application in electrostatics. 