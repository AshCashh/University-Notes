---
Created: 2023-06-27T20:35:53+10:00
Modified: 2024-07-03T19:35:33+10:00
---
 ### Integration By Parts
$$\int uv'\space dx=uv-\int vu'\space dx  $$

### Cos Sin 
$$\cfrac{d}{dx}sin(x)=cos(x)$$
$$\cfrac{d}{dx}cos(x)=-sin(x)$$
$$\int cos(x)\space dx = sin(x)$$
$$\int sin(x)\space dx = -cos(x)$$

### Multivariable Chain Rule 
Suppose:
$$ z=f(x,y), x=x(t)\space and\space y=y(t)$$
If 
$$ z=f(x(t),y(t))=F(t),\space then$$
$$\cfrac{dF}{dt}=\cfrac{\partial f}{\partial x}\cfrac{dx}{dt}+\cfrac{\partial f}{\partial y}\cfrac{dy}{dt}$$
### Multivariable Chain Rule 2
Suppose: 
$$z=f(x,y),\space x=x(s,t)\space and \space y=y(s,t)$$
If
$$z=f(x(s,t),y(s,t))=F(s,t),\space then$$
$$\cfrac{\partial F}{\partial s}=\cfrac{\partial f}{\partial x}\cfrac{\partial x}{\partial s}+\cfrac{\partial f}{\partial y}\cfrac{\partial y}{\partial s} $$
$$\cfrac{\partial F}{\partial t}=\cfrac{\partial f}{\partial x}\cfrac{\partial x}{\partial t}+\cfrac{\partial f}{\partial y}\cfrac{\partial y}{\partial t} $$
### Gradient and Directional Derivative

$$\triangledown f= \cfrac{\partial f}{\partial x}i+\cfrac{\partial f}{\partial y}j$$
$$Duf(x,y)=\triangledown f \times u$$
Remember: $\underline{u} = \cfrac{\underline{v}}{|v|}$

### Critical Point
$$\triangledown f(x_0,\space y_0) = 0$$
### Hessian Determinant Test
$$H(x_0,\space y_0)=det\left(\begin{bmatrix}
f_{xx} & f_{xy} \\
f_{yx} & f_{yy} \\
\end{bmatrix}\right)=f_{xx}f_{yy}-f_{xy}^2$$
Remember: $$det\space A=| A | = \begin{bmatrix}
a & b \\
c & d \\
\end{bmatrix}=ad-bc$$
$$ A^{-1}=\cfrac{1}{ad-bc}\begin{bmatrix}
d & -b \\
-c & a \\
\end{bmatrix}$$

$H>0\space and \space f_{xx}(x_0,\space y_0) > 0=local\space minimum$
$H>0\space and \space f_{xx}(x_0,\space y_0) < 0=local\space maximum$
$H<0=saddle$
$H=0=inconclusive$

### Separation of Variables
Form: 
$$\cfrac{dy}{dt}=f(t)g(t)$$
Becomes:
$$\int \cfrac{1}{g(t)}\cfrac{dy}{dt}dt=\int f(y)\space dy$$
### Integrating Factor
Form:
$$\cfrac{dy}{dt}=f(t)+g(t)y$$
Standard Form:
$$\cfrac{dy}{dt}+p(t)y=f(t)$$
Here: $p(t)=-g(t)$
Multiply both sides by:
$$I(t)=e^{\int p(t) \space dt}$$
Then:
$$\cfrac{d}{dt}\left(I(t)y(t)\right)=I(t)\cfrac{dy}{dt}+\cfrac{dI}{dt}y$$
Integrate **both** sides. Solve 
### Homogeneous ODEs
$$\cfrac{d^2y}{dt^2}+b\cfrac{dy}{dt}+cy=0$$
Characteristic equation:
$$\lambda^2+b\lambda+c=0$$
General Solution:
$$y=C_1e^{\lambda_1t}+C_2e^{\lambda_2t}$$

### Non-Homogeneous ODEs
$$\cfrac{d^2y}{dt^2}+b\cfrac{dy}{dt}+cy=f(t)$$
### Eigenvalue Equation
$$|A-\lambda I | = 0$$
### Eigenvectors
$$(A-\lambda I )v = 0$$
General Solution:
$$y(t)=\sum_{i=1}^n C_iv_ie^{\lambda_it} $$
Initial condition:
$$y_1(0)=2, y_2(0)=0
$$
$$
\begin{bmatrix}
y_1(t)' \\
y_2(t)' \\
\end{bmatrix} = C_1\begin{bmatrix}
v_{11} \\
v_{12} \\
\end{bmatrix}+C_2\begin{bmatrix}
v_{21} \\
v_{22} \\
\end{bmatrix}
$$
$$2=3C_1+C_2$$

# Probability
Notation:
$$AND: \cap $$
$$\\ OR: \cup$$
$$A\cap B = AB$$
Total Probability:
$$Pr(A)=\sum_iPr(A|B_i)Pr(B_i)$$
Events:
$$Pr(A\cup B) = Pr(A)+Pr(B)-Pr(A\cap B)$$
$$Pr(A\cap B)=Pr(A)+Pr(B)-Pr(A\cup B)$$
Independent:
$$Pr[(X_1 > x_1)\cap(X_2 > x_2)]=Pr(X_1 > x_1)Pr(X_2 > x_2)$$
### Bayes' Theorem
$$Pr(B|A)=\cfrac{Pr(A|B)Pr(B)}{Pr(A)}$$
Where the given (the known) is on the right (A)



### Discrete Random Variables
PMF:
$$Pr(X=x)=\cfrac{x}{\sum n}$$
Expected Value: 
$$ \sum x \space p(x)$$
Variance:
$$ \sum (x-\mu)^2\space p(x) = E(X^2)-E(X)^2$$
$$E(X^2)=\sum x^2\space p(x)$$
### Continuous Random Variables
$$Pr(x_1\leq X\leq x_2)=\int_{x_1}^{x_2}f(x)\space dx$$
$$Pr(X> x_1)=\int_{x_1}^{\infty}f(x)\space dx$$
$$Pr(X<x_1)=\int_{\infty}^{x_1}f(x)dx$$
Expected Value:
$$ E(X)=\int_x^\infty x\space f(x)\space dx$$
Variance:
$$\int_x^\infty(X-\mu)^2f(x) dx=E(X^2)-E(X)^2$$
$$E(X^2)=\int_x^\infty x^2f(x)\space dx$$
Median:
$$\int_x^mf(x)\space dx = 0.5$$


### Linear Combinations of Random Variables
Linear function of random variable:
$$E(aX+b)=aE(X)+b$$
$$Var(aX+b)=A^2Var(X)$$
Sum of random variable:
$$E(X+Y)=E(X)+E(Y)$$
$$Var(X+Y)=Var(X)+Var(Y)+2Cov(X,Y)$$
If X and Y are independent: $Var(X+Y)=Var(X)+Var(Y)$
Covariance:
$$Cov(X,Y)=E(XY)-E(X)E(Y)$$
$$=Corr(X,Y)\sqrt{Var(X)Var(Y)}$$
### General Linear Combinations
$$E(aX+bY)=aE(X)+bE(Y)$$
$$Var(aX+bY)=a^2Var(X)+b^2Var(Y)+2abCov(X,Y)$$

### Sample Statistics
Expected value:
$$E(\overline{X})=\mu$$
Variance:
$$s^2=\cfrac{1}{n-1}\left(\sum_{i=1}^nx_i^2-n\overline{x}^2\right)$$
Note: only do $-n\overline{x}^2$ once.

Standard Deviation:
$$s=\sqrt{s^2}$$
### Confidence Intervals 
Choose a high probability ($1-\alpha=0.95$):
Estimates $\mu$ with confidence $1-\alpha$:
$$\overline{X}\pm t_{n-1,\frac{\alpha}{2}}\cfrac{s}{\sqrt{n}}$$
(student's t distribution)
Estimates true proportion $p$ with confidence $1-\alpha$:
$$\hat{p}\pm Z_{\frac{\alpha}{2}}\sqrt{\cfrac{\hat{p}(1-\hat{p}}{n}}$$
where $\hat{p}=\cfrac{X}{n}$
(standard normal distribution)

### Statistical Tests
$$T=\cfrac{\overline{X}-\mu}{\cfrac{s}{\sqrt{n}}}$$
$$Z=\cfrac{\hat{p}-p}{\cfrac{\sqrt{p(1-p)}}{n}}$$
One sided: $p=Pr(Z<Z_{calc})$ or $p=Pr(Z>Z_{calc})$
Two sided: $p=Pr(|Z|>|Z_{calc}|)$ 