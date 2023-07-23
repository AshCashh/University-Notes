#ee
In [[Electrical Engineering]], a Bode Plot is a graph of the [[Frequency Response]] of a system. In this plot, the [[Frequency]] (in Hz) is plotted on the horizontal axis using a logarithmic scale.
![[Pasted image 20230509221902.png|centre|300]]
## Decibels
Unit of gain for [[Transfer Function]] are in decibels (dB).
$$Gain(dB)  = 20log_{10}|H|$$
## 3dB Point
The frequency $f$ at which the transfer function equals:
$$\mathbf{H}(\omega)=\cfrac{1}{1+j}=\cfrac{1}{\sqrt{2}}\angle-45\degree$$
is known as the break frequency, corner frequency, 3dB frequency or half [[Power]] point. This is because the gain at this point is equal to $0.707\approx -3.01dB$, and the angle $-45\degree$ is the halfway point between $0\degree$ and $-90\degree$.

## Calculations
Hertz to rad/s:
$$\omega = f\times2\pi$$
Frequency to Transfer Function:
$$\mathbf{H}(\omega)=\cfrac{v_{out}}{v_{in}}$$
Transfer Function to Gain:
$$Gain=|\mathbf{H}(\omega)|=\sqrt{\Re\{\mathbf{H}(\omega)\}^2+\Im\{\mathbf{H}(\omega)\}^2}$$
Gain to Decibels (dB):
$$Gain(dB)=20log_{10}(Gain)$$
Transfer to Phase:
$$Phase = \angle\mathbf{H}(\omega)$$
 $$=tan^{-1}\cfrac{\Im\{\mathbf{H}(\omega)\}}{\Re\{\mathbf{H}(\omega)\}}$$
##### Bode Plot High Pass Filter Example
Find $v_a(\omega)$ leaving $\omega$ as a variable.
![[Pasted image 20230509222025.png|300]]
$$v_a(\omega)=v_s(\omega)\times\cfrac{R}{R+\cfrac{1}{j\omega C}}$$
Simplify
$$=v_s(\omega)\times\cfrac{Rj\omega}{Rj\omega+\cfrac{1}{C}}$$
Divide by R
$$v_s(\omega)\times\cfrac{j\omega}{j\omega+\cfrac{1}{RC}}$$
Subtitude RC: 
$$v_s(\omega)\times\cfrac{j\omega}{j\omega+100}$$
Apply Transfer function formula: $output=input\times H(\omega)$
$$\therefore\mathbf{H}(\omega)=\cfrac{j\omega}{j\omega+100}$$
Now find $\mathbf{H}(\omega)$ for $f=1$Hz, 10Hz and 100Hz:
![[Pasted image 20230509230231.png]]
![[Pasted image 20230509230307.png]]
