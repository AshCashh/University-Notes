#ee
When signals are neither periodic nor [[Sinusoidal Signals|Sinusoidal]], the [[Fourier Transform]] cannot be used. Any sudden change in a single is regarded as a transient which disturbs the steady-state operation of a system. The Laplace transform is a generalisation of the Fourier transform used to determine the response of a system under both transient and steady-state conditions.

The two-sided Laplace transform of a function $f(t)$ is given by:
$$F(s)=\mathscr{L}\{f(t)\}=\int_{\infty}^{\infty}f(t)e^{-st}\space dt$$
where $s=\sigma+j\omega$ is a complex variable for $\sigma, \omega,\in \mathbb{R}$, measured in rads/s. For causal systems, the lower limit of integration is zero. 

The inverse Laplace transform is given by:   
$$f(t)=\mathscr{L}^{-1}\{F(s)\}= \frac{1}{2\pi j}\int_{\sigma-j\infty}^{\sigma+j\infty}F(s)e^{st}\space ds$$
#### Example
Find the Laplace Transform of:
$$x(t)=e^{-\alpha t},t\leq0,or$$
$$x(t)=e^{-\alpha t}u(t)$$
where $\alpha$ is a real-valued positive constant.
Solution:
$$\begin{align*}
X(s)=\int_0^{\infty}e^{-\alpha t}e^{-st}\space dt\\
X(t)=- \left[\frac{e^{-t(s+\alpha)}}{s+\alpha}\right]_0^{\infty}&= \frac{1}{s+\alpha}
\end{align*}$$
## Conditions 
The Laplace transform converges when:
$$\int_{-\infty}^{\infty}|f(t)e^{-\sigma t}|\space dt<\infty$$
for finite $\sigma$ in rad/s is finite and real.
# Laplace Transform Properties
$$f(t)\overset{\mathscr{L}}{\longleftrightarrow}F(s)$$
## Linearity 
$$af_1(t)+bf_2(t)\overset{\mathscr{L}}{\longleftrightarrow}aF_1(s)+bF_s(t)$$
## Delayed Impulse
$$f(t-a)\overset{\mathscr{L}}{\longleftrightarrow}e^{-as}F(s)$$
## Ramp
$$tu(t)\overset{\mathscr{L}}{\longleftrightarrow} \frac{1}{s^2}$$
## Exponential Decay
$$e^{-at}u(t)\overset{\mathscr{L}}{\longleftrightarrow} \frac{1}{s+a}$$
## Cosine, Sine
$$\begin{align*}
\cos(\omega t)\overset{\mathscr{F}}{\longleftrightarrow} \frac{s}{s^2+\omega^2}\\
\sin(\omega t)\overset{\mathscr{F}}{\longleftrightarrow} \frac{\omega}{s^2+\omega^2}
\end{align*}$$

![[Pasted image 20230922140703.png|800]]

![[Pasted image 20231005191036.png]]
![[Pasted image 20231005191048.png]]
![[Pasted image 20231005191103.png]]

 
![[Pasted image 20230922225037.png]]