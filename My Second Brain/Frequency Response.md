#ee
In [[Signal Processing]] and [[Electronics]], [[Frequency]] response is a measure of the [[Sinusoidal Signals#Magnitude ($V_m$)|Magnitude]] and [[Sinusoidal Signals#Phase ($ phi$)|Phase]] of a system as a function of [[Sinusoidal Signals#Angular Frequency ($ omega$)|Angular Frequency]] ($\omega$). 

The frequency response is widely used in the design and analysis of systems, such as audio and control systems, where they simplify mathematical analysis by converting governing [[Differential Equations]] into algebraic equations. In audio systems, it may be used to minimise audible distortion by designing components (such as microphones, [[Operational Amplifiers]] and loudspeakers) so that the overall response is as flat as possible across the systems bandwidth. In control systems, such as a vehicle's cruise control, it may be used to assess systems stability, often through the use of [[Bode Plots]]. Systems with a specific frequency response can be designed using [[Analogue]] and [[Digital Filters]].

The frequency response is closely related to the [[Transfer Function]] in linear systems, which is the [[Laplace Transform]] of the impulse response. They are equivalent when the real part ($\Re$) of the transfer function's complex variable $s = \Re + j\omega$ is zero.


## Frequency Response Example
Find $v_a(\omega)$ leaving $\omega$ as a variable.
![[Pasted image 20230508161450.png|centre|200]]

Resistor: $\mathbf{Z} = 10k\ohm$
Capacitor: $\cfrac{1}{j\omega C}=\cfrac{1}{j\omega\times10\times10^{-9}}$

Voltage Divider:
$$v_a(\omega) = v_s(\omega)\times\cfrac{\cfrac{1}{j\omega C}}{\mathbf{Z}_R+\cfrac{1}{j\omega C}}$$
Multiply by $j\omega C$
$$=v_s(\omega)\times\cfrac{1}{Rj\omega C + 1}$$
Substitute $RC =10000\times10\times10^{-9}=\cfrac{1}{10000}$.
Note $\omega_0=\frac{1}{RC}$
$$=v_s(\omega)\times\cfrac{1}{\cfrac{j\omega}{10000}  + 1}$$
This function is known as the transfer function:
$$\mathbf{H}(\omega)=\cfrac{v_a(\omega)}{v_s(\omega)}=\cfrac{1}{\cfrac{j\omega}{10000}  + 1}=\cfrac{10000}{j\omega+10000}$$
![[Pasted image 20230508163430.png|centre|300]]

## Simple Circuit Analysis
Find i as a phasor in this circuit:
![[Pasted image 20230508142420.png]]
Firstly, express the voltage source as a phasor and the circuit elements as impedances.

Voltage source: $5\angle 0\degree V$
Resistor: $2\ohm$
Inductor: $j1000\times 1\times 10^{-3}=j1\ohm$

Now express the total impedance as a single phasor value:
i.e. add the two impedances and convert to phasor form.

Magnitude:
$$\sqrt{2^2+1^2} = \sqrt{5}$$
Angle: 
$$tan^{-1}\left(\cfrac{1}{2} \right)=26.6\degree$$
Therefore the phasor is: 
$$\sqrt{5}\angle26.6\degree$$
Using the impedance to find the current:
$$I=\cfrac{V}{Z}= \cfrac{5\angle0\degree}{\sqrt{5}\angle26.6\degree}=\cfrac{5}{\sqrt{5}}\angle(0\degree-26.6\degree)=\sqrt{5}\angle-26.6\degree A$$
Giving the answer as a function of time:
$$\sqrt{5}cos(1000t-26.6\degree)A$$

