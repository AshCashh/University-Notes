#math
The study of differential equations (DE) finds techniques to solve equations relating unknown functions with their derivates. These equations allow us to model and predict the behaviour of systems evolving over time or any other dimension.

## Ordinary and Partial Differential Equations
Differential equations fall into one of two categories:
- Ordinary differential equations (ODE) - derivatives are taken with respect to only one variable 
- Partial differential equations (PDE) - derivatives are taken with respect to several variables.

Some examples of ODEs are shown below:
Exponential growth:
$$ \cfrac{dy}{dt}=ky$$ Newton's Law of cooling:
$$ \cfrac{dy}{dt}=k(A-y)$$
Mechanical vibrations:
$$m\cfrac{d^2x}{dt^2}+c\cfrac{dx}{dt}+kx=f(t)$$
where $x,y,\text{and}\space f$ are functions of time.
Below are some examples of PDEs:
Transport equation:
$$\cfrac{\partial u}{\partial t}+c\cfrac{\partial u}{\partial x} = 0$$
Heat equation:
$$\cfrac{\partial u}{\partial t}=k\cfrac{\partial^2u}{\partial x^2}$$
Laplace's equation:
$$\Delta u=0$$
where $u$ is typically a function of space ($x,y,z$) or space-time ($x,y,z,t$).

# Partial Derivatives
Let $f:\mathbb{R}^2\to\mathbb{R}$ be a [[Scalar Fields|Scalar Field]], then the two partial derivates are:
$$\cfrac{\partial f}{\partial x}=\lim_{h\to0}\cfrac{f(x+h,y)-f(x,y)}{h},$$
$$\cfrac{\partial f}{\partial y}=\lim_{h\to0}\cfrac{f(y+h,x)-f(x,y)}{h},$$
Also use notation $f_x$ and $f_y$ to denote these partial derivates.

The interpretation of $f_x$ is the rate of change of $f$ in the $x$-direction (with respect to $x$) and hold $y$ as a constant.

The geometric interpretation for $f_x$ and $f_y$ are the slopes of the surface $z=f(x,y)$ in the $x$- and $y$-directions, respectively.

### Example
Given $f(x,y)=y^4+2xy^3+x^2y^2$, calculate the partial derivative $f_x$:
$$f_x=2y^3+2xy^2$$


## Order
The order of a differential equation refers to the highest derivative term that appears in the equation.

## Linearity
A linear ODE is defined by a linear polynomial in the unknown function and its derivates:
$$a_n(t)y^{(n)}+\dots +a_2(t)y^{"}+a_1(t)y'+a_0(t)y=f(t)$$
Here the notation $y^{(n)}$ denotes the $n$th derivative of y, and we use this in-place of the apostrophe (') for compactness. Note that the function $y$ itself, can be thought of as the "0"th derivative of $y$. 
Any ODE that cannot be expressed the above form is nonlinear.

## Homogeneity 
Finally, a differential equation is homogeneous when it is an equation consisting only of the unknown function and its derivates. In other words, there are no constant terms (or functions). 
Both ODEs and PDEs are classified by the same rules, below is an example of homogeneous differential equations:
$$ay^{"}+by'+cy=0$$
$$\cfrac{\partial^2u}{\partial x^2}+k\cfrac{\partial^2 u}{\partial t^2}=0$$
