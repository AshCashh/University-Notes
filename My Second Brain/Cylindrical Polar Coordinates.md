#math
# Cylindrical Polar Coordinates in 2D
The cylindrical polar or just polar coordinate system $(r,\theta)$ is defined by:
$$x=r\cos\theta\qquad y=r\sin\theta$$
$$dx\space dy=r\space dr\space d\theta$$
where $r\geq0,0\leq \theta \leq 2\pi$. 
![[Pasted image 20230907174443.png|centre|300]]

For a point $P(r,\theta)$ 
- $r=\sqrt{x^2+y^2}$ is the length of $OP$ 
- $\theta$ is measured anticlockwise from the position $x$-axis to $OP$ 
## Unit Vectors
Unit vectors depend on $\theta$: 
$$\mathbf{e}_r=i\cos(\theta)+j\sin(\theta),$$
$$\mathbf{e}_{\theta}=-i\sin(\theta)+j\cos(\theta)$$
$$\cfrac{\partial\mathbf{e}_r}{\partial \theta}=\mathbf{e}_{\theta},\qquad\cfrac{\partial\mathbf{e}_{\theta}}{\partial \theta}=-\underline{e}_{r}$$
## Gradient
Del operator in polar coordinates is:
$$\nabla = \mathbf{e}_r\cfrac{\partial}{\partial r}+\mathbf{e}_{\theta}\cfrac{1}{r}\cfrac{\partial}{\partial \theta} $$
The gradient of a [[Scalar Fields|Scalar]] function $f(r,\theta)$ is:
$$\nabla f= \mathbf{e}_r\cfrac{\partial f}{\partial r}+\mathbf{e}_{\theta}\cfrac{1}{r}\cfrac{\partial f}{\partial \theta}$$
## Divergence
The divergence of a [[Vector Fields|Vector Field]] $\mathbf{F}=F_r(r,\theta)\mathbf{e}_r+F_{\theta}(r,\theta)\mathbf{e}_{\theta}$ is:
$$\nabla\space \mathbf{F}=\cfrac{\partial F_r}{\partial r}+\cfrac{F_r}{r}+\cfrac{1}{r}\cfrac{\partial F_{\theta}}{\partial\theta}=\cfrac{1}{r}\cfrac{\partial}{\partial r}(rF_r)+\cfrac{1}{r}\cfrac{\partial F_{\theta}}{\partial\theta}$$
## Curl
The curl of a [[Vector Fields|Vector Field]] $\mathbf{F}=F_r(r,\theta)\mathbf{e}_r+F_{\theta}(r,\theta)\mathbf{e}_{\theta}$ is:
$$\nabla\times \mathbf{F}=\cfrac{1}{r}\left(\cfrac{\partial}{\partial r}(rF_{\theta})-\cfrac{\partial F_r}{\partial \theta}\right)\mathbf{k}$$
## Jacobian
The [[Jacobian Matrix and Matrix|Jacobian]] for this transformation is:
$$
J=
\begin{vmatrix}
\cfrac{\partial x}{\partial r} & \cfrac{\partial x}{\partial \theta} \\
\cfrac{\partial y}{\partial r} & \cfrac{\partial y}{\partial \theta} \\
\end{vmatrix}=
\begin{vmatrix}
\cos\theta & -r\sin\theta \\
\sin\theta&r\cos\theta
\end{vmatrix}=r\cos^2\theta+r\sin^2\theta=r
$$
Therefore, the area element is $dA=|J|\space dr\space d\theta=r\space dr\space d\theta$  
# Cylindrical Polar Coordinates in 3D
The polar coordinate system $(r,\theta,z)$ is defined by:
$$x=r\cos(\theta)\qquad y=r\sin(\theta)\qquad z=z$$
![[Pasted image 20230907201940.png|centre|300]]
where $r\geq 0,0\leq\theta\leq 2\pi, -\infty<z<\infty$ 

For a point $P(r,\theta,z)$ 
- $P'$ is the projection of $P(r,\theta,z)$ onto the $xy$-plane
- $r=\sqrt{x^2+y^2}$ is the length of $OP'$ 
- $\theta$ is measured anticlockwise from the positive $x$-axis to $OP'$
## Unit Vectors
As with the 2D case, Unit vectors depend on $\theta$: 
$$\mathbf{e}_r=i\cos(\theta)+j\sin(\theta),$$
$$\mathbf{e}_{\theta}=-i\sin(\theta)+j\cos(\theta)$$
$$\mathbf{e}_z=k
$$$$\cfrac{\partial\mathbf{e}_r}{\partial \theta}=\underline{e}_{\theta},\qquad\cfrac{\partial\mathbf{e}_{\theta}}{\partial \theta}=-\underline{e}_{r},\qquad\cfrac{\partial\mathbf{e}_{z}}{\partial \theta}=0$$
## Gradient
Del operator in polar coordinates is:
$$\nabla = \mathbf{e}_r\cfrac{\partial}{\partial r}+\mathbf{e}_{\theta}\cfrac{1}{r}\cfrac{\partial}{\partial \theta} +\mathbf{e}_z\cfrac{\partial}{\partial z}$$
The gradient of a [[Scalar Fields|Scalar]] function $f(r,\theta)$ is:
$$\nabla f= \mathbf{e}_r\cfrac{\partial f}{\partial r}+\mathbf{e}_{\theta}\cfrac{1}{r}\cfrac{\partial f}{\partial \theta}+\mathbf{e}_z\cfrac{\partial f}{\partial z}$$
## Divergence
The divergence of a [[Vector Fields|Vector Field]] $\mathbf{F}=F_r(r,\theta)\mathbf{e}_r+F_{\theta}(r,\theta)\mathbf{e}_{\theta}+F_z(r,\theta,z)\mathbf{e}_z$ is:
$$\nabla\space \mathbf{F}=\cfrac{\partial F_r}{\partial r}+\cfrac{F_r}{r}+\cfrac{1}{r}\cfrac{\partial F_{\theta}}{\partial\theta}+\cfrac{\partial F_z}{\partial z}=\cfrac{1}{r}\cfrac{\partial}{\partial r}(rF_r)+\cfrac{1}{r}\cfrac{\partial F_{\theta}}{\partial\theta}+\cfrac{\partial F_z}{\partial z}$$
### Example
$$F=re_r+z\sin(\theta)e_{\theta}+rze_r$$

$$
\nabla F=\cfrac{1}{r}\partial_r(r^2)+\cfrac{1}{r}\partial_{\theta}(x\sin\theta)+\partial_z(rz)
$$
$$2+\cfrac{z\cos\theta}{r}+r$$


## Curl
The curl of a [[Vector Fields|Vector Field]] $\mathbf{F}=F_r(r,\theta)\mathbf{e}_r+F_{\theta}(r,\theta)\mathbf{e}_{\theta}+F_z(r,\theta,z)\mathbf{e}_z$ is:
$$
\nabla\times \mathbf{F}=\cfrac{1}{r}
\begin{vmatrix}
\mathbf{e}_r &r\mathbf{e}_{\theta}&\mathbf{e}_z \\
\cfrac{\partial}{\partial r} & \cfrac{\partial}{\partial \theta} &\cfrac{\partial}{\partial z} \\
F_r & rF_{\theta}&F_z
\end{vmatrix}

$$
#### Example
$$F=re_r+z\sin(\theta)e_{\theta}+rze_r$$
$$
\nabla\times \mathbf{F}=\cfrac{1}{r}
\begin{vmatrix}
\mathbf{e}_r &r\mathbf{e}_{\theta}&\mathbf{e}_z \\
\cfrac{\partial}{\partial r} & \cfrac{\partial}{\partial \theta} &\cfrac{\partial}{\partial z} \\
r & rzsin\theta&zr
\end{vmatrix}
$$
$$=\cfrac{1}{r}\left((\partial_{\theta}(zr)-\partial_z(rz\sin\theta))e_r-(\partial_r(zr)-\partial_z(r))e_{\theta}+(\partial_r(z\sin\theta-\partial_{\theta}(r)))e_z\right)$$
$$(0-rsin\theta)e_r-(z-0)e_{\theta}+(z\sin\theta-0)e_z$$

## Jacobian
The [[Jacobian Matrix and Matrix|Jacobian]] for this transformation is:
$$
J=
\begin{vmatrix}
\cfrac{\partial x}{\partial r} & \cfrac{\partial x}{\partial \theta} & \cfrac{\partial x}{\partial z} \\
\cfrac{\partial y}{\partial r} & \cfrac{\partial y}{\partial \theta} & \cfrac{\partial y}{\partial z} \\
\cfrac{\partial z}{\partial r}&\cfrac{\partial z}{\partial \theta}&\cfrac{\partial z}{\partial z}
\end{vmatrix}=
\begin{vmatrix}
\cos\theta & -r\sin\theta &0\\
\sin\theta&r\cos\theta &0\\
0&0&1
\end{vmatrix}=r\cos^2\theta+r\sin^2\theta=r
$$
Therefore, the volume element is $dV=|J|\space dr\space d\theta\space dz=r\space dr\space d\theta\space dz$  
### Example
$$F=re_r+z\sin(\theta)e_{\theta}+rze_r$$



### Q5
$$I=\int_0^{\infty}e^{-x^2}\space dx$$
$$I^2=\int_0^{\infty}\int_0^{\infty}e^{-x^2}e^{-y^2}\space dx\space dy$$
$$=\int_0^{\infty}\int_0^{\infty}e^{-x^2-y^2}\space dx\space dy$$
$$=\int_0^{\frac{\pi}{2}}\int_0^{\infty}e^{-r^2}\space dr\space d\theta$$
$$=\int_0^{\frac{\pi}{2}}\left[-\frac{1}{2}e^{-r^2}\right]_0^{\infty}\space \space d\theta$$
$$=\int_0^{\frac{\pi}{2}}\left[0+\cfrac{1}{2}\right]\space \space d\theta=\left[\cfrac{\theta}{2}\right]_0^{\frac{\pi}{2}}=\pi$$
### Q6
a)
$$\int_{-2}^{2}\int_{-\sqrt}