#math
# Change of Variables in $\mathbb{R}^2$ 
Suppose we wish to change variables via
$$\begin{align}
x&=x(u,v)\\
y&=y(u,v)
\end{align}$$
We define the Jacobian of this transformation as the determinant:
$$
J(u,v)=\begin{vmatrix}
\cfrac{\partial x}{\partial u} & \cfrac{\partial x}{\partial v} \\
\cfrac{\partial y}{\partial u} & \cfrac{\partial y}{\partial v} \\
\end{vmatrix}=\cfrac{\partial x}{\partial u}\cfrac{\partial y}{\partial v}-\cfrac{\partial x}{\partial v}\cfrac{\partial y}{\partial u}
$$
The Jacobian is also denoted by by: $J=\displaystyle\cfrac{\partial(x,y)}{\partial(u,v)}$.
Let $R$ be a region in $\mathbb{R}^2$ and let $R^*$ be the region $R$ described in the $uv$-coordinate system.
Then:
$$\int\int_R\space f(x,y)\space dx \space dy=\int\int_{R^*}\space f(x(u,v),y(u,v)) |J(u,v)| \space du\space dv$$
where $|J(u,v)|$ is the absolute value of the Jacobian for the change of variables.

Need to represent $R^*$ in terms of the new variables $u$ and $v$.

# Change of Variables in $\mathbb{R}^3$ 
Suppose we have a three-dimensional change of variables:
$$\begin{align}
x&=x(u,v,w)\\
y&=y(u,v,w) \\
z&=z(u,v,w)
\end{align}$$
The Jacobian is the determinant:
$$
J(u,v,w)=\begin{vmatrix}
\cfrac{\partial x}{\partial u} & \cfrac{\partial x}{\partial v} & \cfrac{\partial x}{\partial w} \\
\cfrac{\partial y}{\partial u} & \cfrac{\partial y}{\partial v} & \cfrac{\partial y}{\partial w} \\
\cfrac{\partial z}{\partial u} & \cfrac{\partial z}{\partial v} & \cfrac{\partial z}{\partial w}
\end{vmatrix}=
\cfrac{\partial x}{\partial u}\begin{vmatrix}
\cfrac{\partial y}{\partial v} & \cfrac{\partial y}{\partial w} \\
\cfrac{\partial z}{\partial v} & \cfrac{\partial z}{\partial w} \\
\end{vmatrix}
-\cfrac{\partial x}{\partial v}\dots
$$
Also denoted by:  $J=\displaystyle\cfrac{\partial(x,y,w)}{\partial(u,v,w)}$.
Let $V$ be a solid region in $\mathbb{R}^3$ and let $V^*$ be the region $V$ described in the $uvw$-coordinate system.
Then:
$$\int\int\int_V\space f(x,y,w)\space dx \space dy\space dz=\int\int\int_{V^*}\space F(u,v,w) |J(u,v,w)| \space du\space dv\space dw$$
where $F(u,v,w)=f(x(u,v,w),y(u,v,w),z(u,v,w))$ and $|J(u,v,w)|$ is the absolute value of the Jacobian for the change of variables.