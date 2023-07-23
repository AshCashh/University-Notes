#math
A linear second-order [[Differential Equations|Differential Equation]] is a [[Mathematics|Mathematical]] equation of the form:
$$a_2(x)y^"+a_1(x)y'+a_0(x)y=F(x)$$
- If $F(x)=0$, then the equation is [[Differential Equations#Homogeneity|Homogeneous]].
- If $F(x)\neq0$, then the equation is Non-Homogeneous. 

### Initial Value Problem
An initial value problem specifies the value for $y$ and its derivative at a single value of the independent variable:
$$y(x_0) = y_0, \space y'(x_0)=y_1$$
### Boundary Value Problem
A boundary value problem specifies the value for $y$ at two different values of the independent variable:
$$ y(x_0)=y_0,\space y(x_1)=y_1$$
### Superposition Principle
Consider the linear homogenous ODE:
$$a_n(x)y^{(n)}+a_{n-1}(x)y^{(n-1)}+\dots+a_1(x)y'+a_0(x)y=0$$
If $y_1(x),y_2(x),\dots,y_n(x)$ are solutions of the differential equation, then the linear combination of these solutions
$$y(x)=C_1y_1(x)+C_2y_2(x)+\dots+C_ny_n(x)$$
also satisfies the ODE.

# Homogeneous ODEs
A second-order constant-coefficient homogeneous ODE
$$a_2\cfrac{d^2y}{dt^2}+a_1\cfrac{dy}{dt}+a_0y=0$$
has solutions of the form:
$$y=e^{\lambda t}$$
## Characteristic Equation
Substituting this form into the ODE gives the characteristic equation:
$$a_2\lambda^2+a_1\lambda+a_0=0$$
This equation has three distinct cases.
### Real Distinct Roots
For two real and distinct roots, $\lambda_1$ and $\lambda_2$, the general solution is:
$$y=C_1e^{\lambda_1t}+C_2e^{\lambda_2t}$$
### Real Repeated Roots
For the real repeated root, $\lambda$, the general solution is:
$$y=C_1e^{\lambda t}+C_2te^{\lambda t}$$
$$=e^{\lambda t}(C_1+C_2t)$$
### Complex Conjugate Roots
For two complex conjugate roots, $\lambda=\alpha\pm\beta i$, the general solution is:
$$y=e^{\alpha t}(C_1cos(\beta t)+C_2sin(\beta t))$$

# Non-Homogeneous ODEs
A second-order constant-coefficient non-homogeneous ODE
$$a_2y^"+a_1y'+a_0y=F(t)$$
has a general solution of the form:
$$y(t)=y_H(t)+y_P(t)$$
where $y_H(t)$ satisfies the homogeneous version of the ODE (version where $F(t)$ is replaced with zero) i.e.
$$a_2\cfrac{d^2y_H}{dt^2}+a_1\cfrac{dy_H}{dt}+a_0y_H=0$$
and where $y_P(t)$ satisfies the non-homogeneous equation, i.e.
$$a_2\cfrac{d^2y_P}{dt^2}+a_1\cfrac{dy_P}{dt}+a_0y_P=F(t)$$
## Particular Solution 
To find the particular solution $y_P$, we must choose a likely form that it would take. The following table summarises appropriate forms of $y_P$ based on $F(t)$

| Right Hand Side $F(t)$             | Particular Solution $y_P(t)$ of ODE                 |
|-----------------------|--------------------------|
| Constant $a_0$        | $A_0$                    |
| Linear $a_0+a_1t$     | $A_0+A_1t$               |
| Polynomial $a_0+a_1t+\dots+a_nt^n$ | $A_0+A_1t+\dots+A_nt^n$       |
| Exponential $ce^{kt}$ | $Ae^{kt}$ |
| Trigonometric $a_0\cos(kt)+a_1\sin(kt)$ | $A_0\cos(kt)+A_1\sin(kt)$ |

