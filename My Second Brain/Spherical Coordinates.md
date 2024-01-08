#math
The spherical coordinate system $(r,\phi,\theta)$ is defined by the change of variables:
$$
x=r\cos\theta\sin\phi,\qquad y=r\sin\theta\sin\phi,\qquad z=r\cos\phi
$$
where $r\geq 0, 0\leq\phi\leq \pi,0\leq 0\leq 2\pi$ 
![[Pasted image 20230907202131.png|centre|300]]

For a point $P(r,\phi,\theta)$:
- $r$ is measured from the origin $O$ to $P$
- $\phi$ is measured from the positive $z$-axis to $OP$
- $\theta$ is measured anticlockwise from the positive $x$-axis to $OP'$, the projection of $OP$ onto the $xy$-plane
## Unit Vectors
$$\mathbf{e}_r=\sin\phi\cos\theta\mathbf{i}+\sin\phi\sin\theta\mathbf{j}+\cos\phi\mathbf{k}$$
$$\mathbf{e}_{\phi}=cos\phi\cos\theta\mathbf{i}+\cos\phi\sin\theta\mathbf{j}-\sin\phi\mathbf{k}$$
$$\mathbf{e}_{\theta}=-\sin\theta\mathbf{i}+\cos\theta\mathbf{j}$$
## Gradient
$$
\nabla=\mathbf{e}_r \frac{\partial }{\partial r}+\mathbf{e}_{\phi} \frac{1}{r} \frac{\partial }{\partial \phi}+\mathbf{e}_{\theta} \frac{1}{r\sin\phi}\frac{\partial }{\partial \theta}
$$
## Jacobian
$$
J=
\begin{vmatrix}
\cfrac{\partial x}{\partial r} & \cfrac{\partial x}{\partial \phi} & \cfrac{\partial x}{\partial \theta} \\
\cfrac{\partial y}{\partial r} & \cfrac{\partial y}{\partial \phi} & \cfrac{\partial y}{\partial \theta} \\
\cfrac{\partial z}{\partial r} & \cfrac{\partial z}{\partial \phi} & \cfrac{\partial z}{\partial \theta} \\
\end{vmatrix}=
\begin{vmatrix}
\cos\theta\sin\phi & r\cos\theta\cos\phi &-r\sin\theta\sin\phi \\
\sin\theta\sin\phi&r\sin\theta\cos\phi &r\cos\theta\sin\phi \\
\cos\phi&-r\sin\phi&0
\end{vmatrix}=r^2\sin\phi
$$
