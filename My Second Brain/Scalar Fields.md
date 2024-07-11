---
tags: [math]
Created: 2023-08-24T14:56:41+10:00
Modified: 2024-07-03T19:35:33+10:00
---
[[Mathematics]]
A scalar field is a function:
$$f:\mathbb{R}^n\to\mathbb{R}$$
For $n=2$. $f=f(x,y)$.
Two independent variables $x,y$ and $f$ is a function that has $x$ and $y$ as inputs and a single real number as output.

Physical examples of scalar fields are:
The temperature $T(x,y,z)$, the pressure $p(x,y,z)$, the density $\rho(x,y,z)$ of a fluid.

# Directional Derivative 
Let $f:\mathbb{R}^2\to\mathbb{R}$ be a scalar field.

We know $f_x$ and $f_y$ give the rates of change of $f$ in the $x$- and $y$-directions. What about in another direction?

Let the direction in question be defined by the unit vector $\hat{u}=u_1i+u_2j$. Then the directional derivative of $f$ is given by:
$$D_uf=\cfrac{\partial f}{\partial x}u_1+\cfrac{\partial f}{\partial y}u_2$$
Note that if $\hat{u}=i$ then:
$$D_uf=\cfrac{\partial f}{\partial x},$$
and if $\hat{u}=j$, then:
$$D_uf=\cfrac{\partial f}{\partial y}$$
# Gradient
Can write the directional derivative of $f$ in the direction of $\hat{u}=u_1i+u_2j$ as a dot product:
$$D_uf= \cfrac{\partial f}{\partial x}u_1+\cfrac{\partial f}{\partial y}u_2=\left(\cfrac{\partial f}{\partial x}i+\cfrac{\partial f}{\partial y}j\right)\times(u_1i+u_2j)$$
The gradient of $f$ ($\triangledown f$):
$$\nabla f= \cfrac{\partial f}{\partial x}i+\cfrac{\partial f}{\partial y}j$$
Interpretation:
- $\nabla f$ is a vector that points in the direction in which $f$ increases the most. The 
- $|\nabla f|$ is the maximum rate of change (the greatest slope)

## Example 
Find the gradient of $f(x,y)=y^4+2xy^3+x^2y^2$ at $(0,1)$
$$f_x=2y^3+2xy^2,\qquad f_y=4y^3+6xy^2+2x^2y$$
$$\triangledown f=f_xi+f_yj$$
$$\triangledown f(0,1)=2i+4j$$
