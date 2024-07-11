---
tags:
  - ee
  - math
Created: 2024-06-03T10:27:59+10:00
Modified: 2024-07-03T19:35:33+10:00
---
Circuit analysis using [[Laplace Transform]] is performed in the following steps:
1. Convert circuit components, voltages and currents to the Laplace domain
2. Obtain the transfer function in the Laplace domain using [[Mesh Analysis]], nodal analysis or any circuit analysis technique (transfer functions may need to be simplified using partial fraction expansion (PFE)).
3. Take inverse Laplace transform of the solution, to obtain the time domain response.

# Impedance
The [[Impedance]] of an [[Circuit Elements|Circuit Element]] is the ratio of the voltage to the current. Consider the [[Resistor]], [[Capacitor]] and [[Inductor]] definitions:
$$\begin{align*}\\
\text{Resistor: }v(t)&= iR\\
\text{Capacitor: } i(t) &= C \frac{dv}{dt}\\
\text{Inductor: }v(t) &= L \frac{di}{dt}
\end{align*}$$
Taking the Laplace transform gives:
$$\begin{align*}\\
\text{Resistor: }V(s)&= I(s)R\to \frac{V(s)}{I(s)}=R\\
\text{Capacitor: } I(s) &= CsV(s) \to \frac{V(s)}{I(s)}= \frac{1}{sC}\\
\text{Inductor: }V(s) &= LsI(s)\to\frac{V(s)}{I(s)}=sL
\end{align*}$$
