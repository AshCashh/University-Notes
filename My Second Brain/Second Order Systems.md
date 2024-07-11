---
aliases:
  - Second Order System
  - Second Order
tags: [ee, math]
Created: 2024-04-22T12:00:32+10:00
Modified: 2024-07-03T19:35:33+10:00
---
 
A second-order dynamic system is one whose response can be described by a [[Second-Order Differential Equations]].

# General Form 
The general second order transfer functions is:
$$G(s)=\cfrac{\omega^2_n}{s^2+2\zeta\omega_ns+\omega^2_n}$$
where $\zeta=\cfrac{a/2}{\omega_n}\to a=2\zeta\omega_n$ .
Or commonly used for filters:
$$H(s)=\cfrac{\omega_n^2}{s^2+\frac{\omega_n}{Q}s+\omega_n^2}$$
where Q is the Quality Factor such that the greater the value the more "peaky" characteristic.

# Step Response
**Rise Time**: $T_r$ is the time required for the waveform to go from 0.1 to 0.9 of its final value.
**Peak Time**: $T_p$ is the time required to reach the first, or maximum peak.
**Settling Time**: $T_s$ is the time required for the transients damping oscillations to reach and stay within $\pm2$% of the steady state value. 
**Percent Overshoot**: %$OS$ is the amount that the waveform overshoots the steady state or final value at the peak time.

## Underdamped Systems
Specifications for underdamped response:
$$\begin{align}
\text{Settling Time: }T_s&=\cfrac{4}{\zeta\omega_n}\\
\text{Peak Time: }T_p&=\cfrac{\pi}{\omega_n\sqrt{1-\zeta^2}}\\
\%OS&=\cfrac{c(t)_{max}-c(t)_{final}}{c(t)_{final}}\times 100\\
&=e^{\cfrac{\zeta\pi}{\sqrt{1-\zeta^2}}}\times 100
\end{align}
$$

![[Pasted image 20231015163056.png]]



