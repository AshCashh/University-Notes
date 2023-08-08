#math
A Fourier series is an expansion of a periodic function, in terms of an infinite sum of [[Trigonometric Functions]]. 

## Fourier Series Expansion
The Fourier Series Expansion of a function $x(t)$ on the interval $[t_0,t_0+T]$ is given by:
$$x_F(t)=a_0+\sum_{n=1}^{\infty}(a_n\space cos(2\pi nf_0t)+b_n\space sin(2\pi nf_0t))\tag{1}$$
where $n$ is any positive integer and $f_0=\cfrac{1}{T}$, $T$ is the period of the function. The coefficients are given by:
$$
\begin{align}
&a_0=\cfrac{1}{T}\int_{t_0}^{t_0+T}x(t)\space dt\tag{2} \\
&a_n=\cfrac{2}{T}\int_{t_0}^{t_0+T}x(t)\space cos(2\pi nf_0t)\space dt\tag{3} \\
&b_n = \cfrac{2}{T}\int_{t_0}^{t_0+T}x(t)\space sin(2\pi nf_0t)\space dt  \tag{4}\\
\end{align}
$$
where $t_0$ is any value of $t$ (often chosen to be: $t_0=0$ or $t_0=\frac{-T}{2}$. $a_0$ is the average value over one period. It also represents the DC component of a signal.

### Example
A square wave function $f(t)$ is defined as:
$$
f(t)=
\begin{cases}
-1, &-\pi<t<0 \\
1, &0<t<\pi
\end{cases}
$$
with $f(t)=f(t+2\pi)$. Compute the Fourier series for $f(t)$

Choose $t_0=\frac{T}{2}=-\pi$ and evaluate the constants:
$$\begin{align}
a_0&=\cfrac{1}{T}\int_{-\frac{T}{2}}^{\frac{T}{2}}f(t)\space dt \\
&=\cfrac{1}{2\pi}\int^0_{-\pi}(-1)\space dt+\cfrac{1}{2\pi}\int_0^{\pi}1\space dt \\
&=\cfrac{1}{2\pi}[-t]_{-\pi}^0+\cfrac{1}{2\pi}[t]_0^{\pi} \\
&=\cfrac{1}{2\pi}[-\pi+\pi] \\
&=0 \\
\\
a_n&=\cfrac{2}{T}\int_{-\frac{T}{2}}^{\frac{T}{2}}f(t)\space cos\left(\cfrac{2\pi nt}{T}\right)\space dt,\qquad\text{for $n\geq1$} \\
&=\cfrac{1}{\pi}\int_{-\pi}^0-cos(nt)\space dt+\cfrac{1}{\pi}\int_{0}^{\pi}cos(nt)\space dt\\
&=\cfrac{1}{\pi}\left[\cfrac{-sin(nt)}{n}\right]_{-\pi}^0+\cfrac{1}{\pi}\left[\cfrac{sin(nt)}{n}\right]_0^{\pi} \\
&=0 \\
\\
b_n&=\cfrac{2}{T}\int_{-\frac{T}{2}}^{\frac{T}{2}}f(t)\space sin\left(\cfrac{2\pi nt}{T}\right)\space dt,\qquad\text{for $n\geq1$} \\
&=\cfrac{1}{\pi}\int_{-\pi}^0-sin(nt)\space dt+\cfrac{1}{\pi}\int_{0}^{\pi}sin(nt)\space dt\\
&=\cfrac{1}{\pi}\left[\cfrac{-cos(nt)}{n}\right]_{-\pi}^0+\cfrac{1}{\pi}\left[\cfrac{cos(nt)}{n}\right]_0^{\pi} \\
&=\cfrac{1}{\pi}\left(\cfrac{1}{n}-\cfrac{cos(-n\pi)}{n}\right)+\cfrac{1}{\pi}\left(\cfrac{-cos(n\pi)}{n}+\cfrac{1}{n}\right) \\
&=\cfrac{2(1-cos(n\pi))}{n\pi} \\
&=\cfrac{2(1-(-1)^n)}{n\pi} \\

\end{align}

$$
The Fourier series for $f(t)$ is:
$$\begin{align}
f(t)&=a_0+\sum_{n=1}^{\infty}(a_n\space cos(n\omega t)+b_n\space sin(n\omega t)) \\
&=\cfrac{4\space sin(t)}{\pi}+\cfrac{4\space sin(3t)}{3\pi}+\cfrac{5\space sin(5t)}{5\pi}+\dots

\end{align}
$$
![[Pasted image 20230807203637.png]]


# Complex Fourier Series
The Complex Fourier Series Expansion is a concise form of the Fourier series expansion that uses complex exponentials with a single unknown coefficient.
$$s(t)=\sum_{n=-\infty}^{\infty}c_ne^{j2\pi nf_0t}\tag{1}$$
where
$$
c_n=\cfrac{1}{T}\int^{t_0+T}_{t_0}s(t)e^{-j2\pi nf_0t}\space dt \tag{2}
$$
This representation is compact using complex harmonic exponentials as the basis [[Functions]]. The mean term remains the same: $c_0=a_0$ that is when $n=0$.

A good way to understand the relationship between the trigonometric and complex exponential Fourier series is to look at how [[Euler's Formula]] fits into $(1)$ and $(2)$.

Euler's formula,
$$e^{j2\pi nf_0t}=cos(2\pi nf_0t)+j\space sin(2\pi nf_0t)$$
Substituted into $(2)$, yields
$$c_n=\cfrac{1}{T}\underbrace{\int_{t_0}^{t_0+T}s(t)\space cos(2\pi nf_0t)\space dt}_{\text{Even, cosine basis, real part}}-\cfrac{j}{T}\underbrace{\int_{t_0}^{t_0+T}s(t)\space sin(2\pi nf_0t)\space dt}_{\text{Odd, sine basis, imaginary part}}$$
### Alternate Expression 
$$s(t)=c_0+\sum_{\underbrace{n=-\infty}_{n\neq0}}^{\infty}c_ne^{j2\pi nf_0t}$$
Means that $c_0$ is evaluated separately, then the integral is used to evaluate all harmonics.
$$c_0 =\cfrac{1}{T}\int_{t_0}^{t_0+T}s(t)\space dt$$
Note that the signal is decomposed into an infinite sum of positive and negative harmonics of the fundamental frequency ($f_0$).
$$c_{-n}=c_n^*$$
The * denotes [[Complex Numbers#Complex Conjugate|Complex Conjugate]]. Any real valued signal will consist of positive and negative frequency components.

## Magnitude and Phase Spectra
As $c_n$ is a complex number, consider the polar representation of $c_n$:
$$c_n=|c_n|e^{j\theta_n}$$so that the **Magnitude Spectra** is given by $|c_n|$ and the phase spectra is given by $\theta_n$. 

The plot of $|c_n|$ against frequency ($n$) is known as the Magnitude Spectrum and the plot of $\theta_n$ against frequency ($n$) is called the Phase Spectrum.

## [[Functions#Even and Odd Functions|Even and Odd Functions]]
Magnitude spectrum is an even function of $f$ 
Phase spectrum is an odd function of $f$ 
$$|c_n| =|c_{-n}|,\quad \theta_n=-\theta_n$$
![[Pasted image 20230802192834.png|centre|400]]
### EFS Example 1: Odd square wave
![[Pasted image 20230802193010.png|400]]
First evaluate the average of this signal ($c_0$):
$$
\begin{align}
c_0 &=\cfrac{1}{T}\int_{t_0}^{t_0+T}x(t)\space dt \\
&=\cfrac{1}{T}\left[\int_0^{\frac{T}{2}}x(t)\space dt + \int_{\frac{T}{2}}^Tx(t)\space dt\right] \\
&=\cfrac{1}{T}\left[\int_0^{\frac{T}{2}}1\space dt+\int_{\frac{T}{2}}^T-1\space dt\right]=0
\end{align}
$$
Next $c_n$:
$$
\begin{align}
c_n&=\cfrac{1}{T}\left[\int_0^{\frac{T}{2}}1e^{-j2\pi nf_0t}\space dt+\int_{\frac{T}{2}}^T-1e^{-j2\pi nf_0t}\space dt\right] \\ 
&=\cfrac{1}{T}\left[\int_0^{\frac{T}{2}}e^{-j2\pi nf_0t}\space dt-\int_{\frac{T}{2}}^Te^{-j2\pi nf_0t}\space dt\right] \\ 
&=\cfrac{1}{T}\left[\int_0^{\frac{T}{2}}e^{\frac{-j2\pi nt}{T}}\space dt-\int_{\frac{T}{2}}^Te^{\frac{-j2\pi nt}{T}}\space dt\right] \\ 
&=\cfrac{1}{T}\left(\left[\frac{T}{-j2\pi n}e^{-\frac{j2\pi n t}{T}}\right]_0^{\frac{T}{2}}+\left[\frac{T}{-j2\pi n}e^{-\frac{j2\pi n t}{T}}\right]_0^{\frac{T}{2}}\right) \\
&=\cfrac{1}{-j2\pi n}\left(\left[ e^{-\frac{j2\pi n \left(\frac{T}{2}\right)}{T}}-e^{-\frac{j2\pi n \left(0\right)}{T}}\right]+\left[ e^{-\frac{j2\pi n \left(\frac{T}{2}\right)}{T}}-e^{-\frac{j2\pi n \left(0\right)}{T}}\right]\right)\\
&=\cfrac{1}{-j2\pi n}([ e^{-j\pi n}-e^{0}]+[e^{-j\pi n}-e^{-j2\pi n}]) \\
&=\cfrac{1}{-j2\pi n}([ e^{-j\pi n}-1]+e^{-j\pi n}[e^{j2\pi n}-1]) \\
&=\cfrac{1}{-j2\pi n}(-2+(e^{j\pi n}+e^{-j\pi n})) \\
&=\cfrac{1}{-j2\pi n}(2-(e^{j\pi n}+e^{-j\pi n})) \\
&=\cfrac{1}{j\pi n}\left(\frac{2-(e^{j\pi n}+e^{-j\pi n})}{2}\right) \\
&=\cfrac{1}{j\pi n}(1-cos(\pi n)) \\
\end{align}
$$
