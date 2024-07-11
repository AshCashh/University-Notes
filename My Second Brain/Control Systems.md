---
aliases:
  - LTI System
tags:
  - ee
  - math
Created: 2023-08-29T22:53:01+10:00
Modified: 2024-07-03T19:35:33+10:00
---
A control system is a system in which a given initial state will always produce the same output. The system $H$ maps the input signal $x(t)$ to the output $y(t)$. 

## Linear Time-Invariant System
A system $H$ is **linear time-invariant** (LTI) if it satisfies the following properties:
1. The system is linear if it satisfies the superposition principle.
   $$\begin{align}
\text{Input: }x(t)&=a_1x_1(t)+a_2x_2(t) \\
\text{Output: }y(t)&=a_1y_1(t)+a_2y_2(t) \\
\end{align}
$$
	Given an input $x$ which consists of a linear combination of signals, the output $y$ of the system is the linear combination of the system's responses to each signal separately.
2. The system is **time-invariant** if a delay in the input produces a delay in the output
      $$\begin{align}
\text{Input: }x(t)&=x(t-t_0) \\
\text{Output: }y(t)&=y(t-t_0) \\
\end{align}
$$

## Signal Approximation
Consider the [[Fourier Transform#Dirac Delta Function|Impulse Function]] $p$ such that:
$$
\begin{align}
p(t)&=
\begin{cases}
\frac{1}{\Delta t}\qquad 0<t<\Delta t \\
\space0\qquad\space\space \text{otherwise}
\end{cases} \\
p(t-t_0)&=
\begin{cases}
\frac{1}{\Delta t}\qquad t_0<t<t_0+\Delta t \\
\space0\qquad\space\space \text{otherwise}
\end{cases} \\
\end{align}
$$
Given a signal $x(t)$ sampled at the rate $1/\Delta t$ (Hz), we can approximate $x(t)$ by:
$$
x(t)\approx\sum_{k=-\infty}^{\infty}x(k\Delta t)\space p(t-k\Delta t)
$$
where $t=k\Delta t$ is the time at the start of each interval where the signal $x(t)$ is sampled. If we consider the limits as $\Delta t\to0$, we obtain the following:
$$
\begin{align}
x(t)&=\lim_{\Delta t\to0}\sum_{k=-\infty}^{\infty}x(k\Delta t)\space p(t-k\Delta t)\Delta t \\
&=\int_{-\infty}^{\infty}x(\tau)\space\delta (t-\tau)\space d\tau
\end{align}
$$
where $\Delta t\to d\tau$, and $k\Delta t\to\tau$. This equivalent form represents $x(t)$ as a linear combination of shifted impulses $\delta(t-\tau)$ with weights $x(\tau$).

# Impulse Response
A system's **impulse response** $h(t)$ is defined as:
$$\begin{align}
\text{Input: }x(t)&=\delta(t) \\
\text{Output: }y(t)&=h(t) \\
\end{align}
$$
that is, the response to an impulse input signal. Passing the signal $x(t)$ into this system gives the following result:
$$
\begin{align}
\text{Input: }x(t)&=\lim_{\Delta t\to0}\sum_{k=-\infty}^{\infty}x(k\Delta t)\space p(t-k\Delta t)\Delta t \\
\text{Output: }y(t)&=\lim_{\Delta t\to0}\sum_{k=-\infty}^{\infty}x(k\Delta t)\space h_p(t-k\Delta t)\Delta t \\
&=\int_{-\infty}^{\infty}x(\tau)\space h (t-\tau)\space d\tau
\end{align}
$$
# Convolution
The integral seen in the previous section is known as the **convolution** of $x$ with $h$, denoted by an asterisk ($*$).
$$y(t)=x(t)\space * \space h(t)=\int_{-\infty}^{\infty}x(\tau)\space h (t-\tau)\space d\tau$$
Therefore
$$\begin{align}
\text{Input: }x(t)&=x(t)\space *\space \delta(t) \\
\text{Output: }y(t)&=x(t)\space *\space h(t) \\
\end{align}
$$
The convolution between two signals $x(t)$ and $y(t)$ is given by:
$$x(t)\space *\space y(t)=\int_{-\infty}^{\infty}x(\tau)\space y (t-\tau)\space d\tau$$
Or equivalent:
$$
y(t)\space * \space x(t)=\int_{-\infty}^{\infty}y(\tau)\space x (t-\tau)\space d\tau
$$
Convolution is equivalent to multiplication in the frequency domain:
$$\mathscr{F}(x(t)\space *\space y(t))=X(f)\space Y(f)$$
# Stability and Causality 
#### Stability
An LTI system is Bounded Input Bounded Output (BIBO) stable if and only if:
$$\int_{-\infty}^{\infty}|h(t)|\space dt <\infty$$
#### Causality
Causality means that the output at time $t$ does not depend on future values of the input signal. In terms of the impulse response, this means that $h(t)=0$ for $t<0$. 

# Week 11 EGB242
]] 
