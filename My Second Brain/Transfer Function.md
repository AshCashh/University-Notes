#ee
In [[Electrical Engineering]], a transfer function (also known as system function or network function) of a system, sub-system or component is a [[Mathematics|Mathematical]] function that models the systems output for each possible input. 

The transfer function of a system is given by:
$$\mathbf{H}(\omega)=\cfrac{\mathbf{Y}(\omega)}{\mathbf{X}(\omega)}=\cfrac{output}{input}$$
where $\mathbf{Y}$ is the output and $\mathbf{X}$ is the input of the system

$\mathbf{H}(\omega)$ has both [[Sinusoidal Signals#Magnitude ($V_m$)|Magnitude]] and angle, where magnitude is gain and angle is [[Sinusoidal Signals#Phase ($ phi$)|Phase]] shift.

##### Transfer Function Example
Find $H(\omega)$ for $f=5000Hz$ using the transfer function in previous example
$$\mathbf{H}(\omega)=\cfrac{10000}{j\omega+10000}$$
Remember: $\omega=2\pi f$, therefore:
$$\omega=2\times5000\pi =10000\pi= 31416 \space rads^{-1}$$
Substitude:
$$\mathbf{H}(10000\pi)=\cfrac{10000}{j10000\pi+10000}=\cfrac{1}{j\pi+1}=0.303\angle-72.3\degree$$

##### Applying Transfer Function Example
Multiply by the gain $v_s$
Add the phase shift to time term.

Remember the gain is the $\mathbf{H}(\omega)$ magnitude and by rearranging the function we can get the output.
$$v_a = \mathbf{H}(\omega)\times v_s$$
The $v_s$ gain is 10 and $\mathbf{H}(\omega)$ is $0.303\angle-72.3\degree$, we get:
$$v_a = 0.303\angle-72.3\degree \times 10$$
$$=3.03cos(31416t-72.3\degree)\space or\space 3.03\angle-72.3\degree$$
![[Pasted image 20230508173422.png]]
