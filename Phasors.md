#ee
Phasors use complex numbers to represent [[Sinusoidal Signals]] and [[Circuit Elements]]

## Phasor Transforms
A sinusoidal signal can be converted to a phasor using the phasor transform
Based on [[Euler's Formula]]:
$$e^{\pm j\theta}=cos\theta \pm j sin\theta$$
We can write:
$$\mathbf{V}=V_me^{j\phi}=P\{V_mcos(\omega t+\phi)\}$$
Here $\mathbf{V}$ is the phase-domain representation of the time-domain signal $v(t)$. The magnitude and phase of a phasor can be used to represent a phasor in polar form:
$$V_m\angle\phi$$
#### Example

$$P\{20cos(\omega t+30\degree)\} = 20\angle 30\degree$$
Find the phasor transform for: $5cos(\omega t-40\degree)$
Answer: $P\{5cos(\omega t-40\degree)\} = 5\angle -40\degree$

## Phasors Operations
Phasors have magnitude and direction (phase) so behave like vectors. Therefore they can convert to rectangular form:
$$\mathbf{V}=V_mcos\phi+jV_msin\phi$$
in polar form, the magnitude is given by:
$$\|\mathbf{V}\|=V_m=\sqrt{\Re\{\mathbf{V}\}^2+\Im\{\mathbf{V}\}^2}$$
and the angle:
$$arg(\mathbf{V})=\phi=arctan\cfrac{\Im\{\mathbf{V}\}}{\Re\{\mathbf{V}\}}$$
Where $\Re\{\mathbf{V}\}$ is the real component i.e $V_mcos\phi$ and $\Im\{\mathbf{V}\}$ is the imaginary component i.e $V_msin\phi$. $arctan$ is $tan^{-1}$

### Addition with Phasors
Phasors in rectangular form can be added using their real and imagarinary components.
$$\mathbf{A}+\mathbf{B}=\Re\{\mathbf{A}+\mathbf{B}\}+\Im\{\mathbf{A}+\mathbf{B}\}$$
$$=(A_mcos(\phi_1)+B_mcos(\phi_2))+j(A_msin(\phi_1)+B_msin(\phi_2))$$
##### Addition Example
![[Pasted image 20230430194209.png|200]]
We want to find the output voltage: $v_a + v_b$
First find $v_a$ and $v_b$ as phasors:
$$V_a = 20\angle-30\degree$$
$$V_b=40\angle60\degree$$
Convert to polar form:
$$V_a = 20cos(-30\degree)+j20sin(-30\degree)$$
$$ =17.32-j10V$$
$$V_b = 40cos(60\degree)+j40sin(40\degree)$$
$$=20+j34.64V$$
Add real and imaginary components:
$$V_a+V_b=37.32+j24.64V$$
Convert back into phasors:
$$V_m=\sqrt{37.32^2+24.64^2}=44.72V$$
$$\phi=tan^{-1}\left(\cfrac{24.64}{37.32}\right)=33.43\degree$$
Together:
$$V_a+V_b=44.72\angle33.43\degree$$
### Multiplication with Phasors
Phasors in polar form can be multiplied using their magnitudes and phases:
$$\mathbf{AB}=\|\mathbf{A}\|\|\mathbf{B}\|\angle arg(\mathbf{A})+arg(\mathbf{B})$$
$$=A_mB_m\angle\phi_A+\phi_B$$
##### Multiplication Example
$\mathbf{A}=2\angle45\degree$
$\mathbf{B}=4\angle30\degree$
$$\mathbf{AB}=(2\times4)\angle(45+30)\degree$$
$$=8\angle75\degree$$
### Division with Phasors
$$\cfrac{\mathbf{B}}{\mathbf{A}}=\cfrac{\|\mathbf{B}\|}{\|\mathbf{A}\|}\angle arg(\mathbf{B})-arg(\mathbf{A})$$
$$=\cfrac{B_m}{A_m}\angle\phi_B-\phi_A$$
##### Division Example
$\mathbf{A}=2\angle45\degree$
$\mathbf{B}=4\angle30\degree$
$$\cfrac{\mathbf{A}}{\mathbf{B}}=\left(\cfrac{4}{3}\right)\angle(30-45)\degree$$
$$=2\angle-15\degree$$



