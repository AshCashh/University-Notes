#math
A vector field is a function:
$$\mathbf{F}:\mathbb{R}^n\to\mathbb{R}^n$$
For $n=2$, $\mathbf{F}=F_1(x,y)i+F_2(x,y)j$:
- Two independent variables $x,y$ 
- $\mathbf{F}$ is a 2-component vector field $(F_1,F_2$) in 2D where each component is a scalar function of $x,y$

For $n=3$, $\mathbf{F}=F_1(x,y,z)i+F_2(x,y,z)j+F_3(x,y,z)k$:
- Three independent variables $x,y,z$ 
- $\mathbf{F}$ is a 3-component vector field ($F_1,F_2,F_3$) is 3D where each component is a scalar function of $x,y,z$ 

Physical examples of vector fields are:
- A velocity field $\mathbf{v}$ in a fluid
- A force field $\mathbf{F}$, perhaps due to an electrical charge
- Electrical field intensity $\mathbf{E}$ (or just electrical field)
- Magnetic flux density $\mathbf{B}$ (or just magnetic field).

# Divergence of a Vector Field
Let $\mathbf{F}:\mathbb{R}^3\to\mathbb{R}^3$ be a vector field with
$$\mathbf{F}(x,y,z)=F_1(x,y,z)i+F_2(x,y,z)j+F_3(x,y,z)k$$
The divergence of $\mathbf{F}$ (div $\mathbf{F}$) is:
$$
\begin{align}
\nabla\space \mathbf{F} &= \left(\frac{\partial}{\partial x}i+\frac{\partial}{\partial y}j+\frac{\partial}{\partial z}k\right)\space(F_1i+F_2j+F_3k) \\
&=\frac{\partial F_1}{\partial x}+\frac{\partial F_2}{\partial y}+\frac{\partial F_3}{\partial z}
\end{align}
$$
Note: $\nabla\space \mathbf{F}$ is a scalar. 

If $\nabla\space \mathbf{F}=0$, that is the divergence is 0, then it is solenoidal.
### Example
Let $\mathbf{F}=x^2y\mathbf{i}+z\mathbf{j}+xyz\mathbf{k}$, calculate $\nabla\space\mathbf{F}$
$$
\begin{align}
\nabla\space \mathbf{F} &= \frac{\partial}{\partial x}(x^2y)+\frac{\partial}{\partial y}(z)+\frac{\partial}{\partial z}(xyz) \\
&=2xy+0+xy \\
&=3xy
\end{align}
$$


## Physical Interpretation of $\nabla\space \mathbf{F}$ 
If $\mathbf{F}$ is the velocity field of a fluid, then $\nabla\space F$ at a point $P$ measures the tendency of the fluid to diverge away from $P$ (if $\nabla\space F>0$ ), or to accumulate towards $P$ (if $\nabla\space F<0$).

# Curl of a Vector Field
Let $\mathbf{F}:\mathbb{R}^3\to\mathbb{R}^3$ be a vector field with
$$\mathbf{F}(x,y,z)=F_1(x,y,z)i+F_2(x,y,z)j+F_3(x,y,z)k$$
The curl of $\mathbf{F}$ is:
$$
\begin{align}
\nabla\times\mathbf{F}&= \left(\frac{\partial}{\partial x}i+\frac{\partial}{\partial y}j+\frac{\partial}{\partial z}k\right)\times(F_1i+F_2j+F_3k) \\
&= \begin{array}{|ccc|}
  \mathbf{i}&\mathbf{j}&\mathbf{k}\\
  \cfrac{\partial}{\partial x}&\cfrac{\partial}{\partial y}&\cfrac{\partial}{\partial z} \\
  F_1&F_2&F_3
\end{array} \\
&=\left(\cfrac{\partial F_3}{\partial y}-\cfrac{\partial F_2}{\partial z}\right)\mathbf{i}-\left(\cfrac{\partial F_3}{\partial x}-\cfrac{\partial F_1}{\partial z}\right)\mathbf{j}+\left(\cfrac{\partial F_2}{\partial x}-\cfrac{\partial F_1}{\partial y}\right)\mathbf{k}
\end{align}
$$
Note: $\nabla\times \mathbf{F}$ is a vector field. 
### Example
![[Pasted image 20230824192100.png]]



## Physical Interpretation of $\nabla\times \mathbf{F}$ 
If $\mathbf{F}$ is the velocity field of fluid in a lake. Drop a small twig into the lake. Then $\nabla\times \mathbf{F}$ measures how quickly and in what orientation the twig rotates as it moves.
![[Pasted image 20230824192633.png]]