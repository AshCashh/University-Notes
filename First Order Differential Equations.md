#math
A first order [[Differential Equations|Differential Equation]] is an equation of the form $\cfrac{dy}{dx}=f(x,y)$. Where two variables ($x, y$) with its function $f(x,y)$ are defined on a region in the $xy$-plane. 

## Separable ODEs
For a differential equation of the form:
$$\cfrac{dy}{dx}=p(x)q(y),$$
a separation of variables followed by an integration with respect to $x$ yields an implicit solution.
$$\int \cfrac{1}{q(y)}\cfrac{dy}{dx}dx=\int p(x)dx$$

## Linear ODEs (Integrating Factor)
For a differential equation of the form:
$$\cfrac{dy}{dx}=f(x)+g(x)y$$
It's standard form becomes:
$$\cfrac{dy}{dx}+p(x)y=f(x)$$
Here: $p(x)=-g(x)$

we can use the integrating factor:  
$$I(x)=e^{\int p(x)dx}$$
so that:
$$y(x)=\cfrac{1}{I(x)}\int I(x)f(x)dx$$
