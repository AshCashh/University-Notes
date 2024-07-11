---
tags: [math]
Created: 2023-08-10T13:21:14+10:00
Modified: 2024-07-03T19:35:33+10:00
---
The Fourier Transform ($\mathscr{F}$) allows us to extend the techniques used in [[Fourier Series]] representations of [[Functions]] to non-periodic signals.

The Fourier transform of a function $x(t)$ is defined by:
$$\mathscr{F}\{x(t)\}=X(f)=\int_{-\infty}^{\infty}x(t)e^{-j2\pi ft}\space dt$$
where $G(f)$ is a complex function, the magnitude is an even function of frequency and the angle or phase is an odd function of frequency.

The inverse Fourier transform ($\mathscr{F}^{-1}$) of a function $X(f)$ is defined by:
$$\mathscr{F}^{-1}\{X(f)\}=x(t)=\int_{-\infty}^{\infty}X(f)e^{j2\pi ft}\space df$$
This integral transform is commonly represented as a "Fourier pair" using the following notation.
$$x(t)\overset{\mathscr{F}}{\longleftrightarrow}X(f)$$
$X(f)$ is referred to as the Spectrum of $x(t)$.

## Example
Consider the Gate function shown below:
![[Pasted image 20230810133842.png|200]]
$$\begin{align}
\mathscr{F}\{\Pi_T(t)\}=\Pi_T(f)&=\int_{-\infty}^{\infty}\Pi_T(t)e^{-j2\pi ft}\space dt \\
\Pi_T(f)&=\int_{-T/2}^{T/2}\Pi_T(t)e^{-j2\pi ft}\space dt \\
&=\cfrac{1}{-j2\pi f}(e^{-j2\pi f(T/2)}-e^{-j2\pi f(-T/2)}) \\
&=\cfrac{1}{-j2\pi f}(e^{-j\pi fT}-e^{j\pi fT}) \\
&=\cfrac{1}{\pi f}\left(\cfrac{e^{-j\pi fT}-e^{j\pi fT}}{-j2}\right)=\cfrac{1}{\pi f}\left(\cfrac{e^{j\pi fT}-e^{-j\pi fT}}{j2}\right) \\
&=\cfrac{1}{\pi f}sin(\pi fT)\\
&=T\cfrac{sin(\pi fT)}{\pi fT} \\
&=T\space sinc(fT)
\end{align}
$$
The Fourier transform of the gate function results in the "sinc function", $sinc(\theta)=\frac{sin(\pi\theta)}{\pi\theta}$ which is known as the normalised sin function

# Fourier Transform Properties
Fourier transform has a set of important properties which can facilitate signal analysis. These include: Linearity, Time delay, Scaling, Time shift, Frequency shift, Time domain differentiation.

## Linearity
$$ax_1(t)+bx_2(t)\overset{\mathscr{F}}{\longleftrightarrow}aX_1(f)+bX_2(f)$$
$$x_1(t)x_2(t)\overset{\mathscr{F}}{\longleftrightarrow}X_1(f)X_2(f)$$
$$
ax_1(t)\overset{\mathscr{F}}{\longleftrightarrow}aX_1(f)
$$
##### Example:
If 
$$\begin{align}
&g_1(t)\longleftrightarrow G_1(f), \space g_2(t)\longleftrightarrow G_2(f) \\
\\
&\mathscr{F}[a_1g_1(t)+a_2g_2(t)]=a_1G_1(f)+a_2G_2(f) \\
\end{align}
$$
If the Fourier transform of $g_1(t)$ and $g_2(t)$ are $G_1(f)$ and $G_2(f)$, respectively then:
- The Fourier transform of ${Ag_1(t)\pm Bg_2(t)}$ is equal to ${AG_1(f)\pm BG_2(f)}$.

The Fourier transform of the sum of two functions is the sum of their Fourier transforms.
If a time domain function is scaled by a factor $\alpha$, its Fourier transform is also scaled by the same factor.

## Complex Conjugate
$$
x^*(t)\overset{\mathscr{F}}{\longleftrightarrow}X^*(-f)
$$
---------- 
## Time Shift
$$x(t-t_0)\overset{\mathscr{F}}{\longleftrightarrow}e^{-j2\pi ft_0}X(f)$$
## Time Reversal
$$
x(-t)\overset{\mathscr{F}}{\longleftrightarrow}X(-f) 
$$
$$x(-t)\overset{\mathscr{F}}{\longleftrightarrow}X^*(\omega)
$$
## Frequency Shift
$$e^{j2\pi f_0t}x(t)\overset{\mathscr{F}}{\longleftrightarrow}X(f-f_0)$$
#### Example
Find the Fourier transform by first principles of $g(t)$, where
$$
\begin{align}
g(t)&=x(t)e^{j2\pi f_0t} \\
G(f)&=\int_{-\infty}^{\infty}g(t)e^{-j2\pi ft}\space dt \\
&=\int_{-\infty}^{\infty}(x(t)e^{j2\pi f_0t})e^{-j2\pi ft}\space dt \\
&=\int_{-\infty}^{\infty}x(t)e^{-j2\pi t(f-f_0)} \space dt \\
\\
&G(f)=X(f-f_0)
\end{align}
$$
Find the Fourier transform by first principles of $h(t)$, where
$$
\begin{align}
h(t)&=x(t)e^{-j2\pi f_0t} \\
H(f)&=\int_{-\infty}^{\infty}h(t)e^{-j2\pi ft}\space dt \\
&=\int_{-\infty}^{\infty}(x(t)\space e^{-j2\pi f_0t})e^{-j2\pi ft}\space dt \\
&=\int_{-\infty}^{\infty}x(t)e^{-j2\pi t(f+f_0)} \space dt \\
\\
&H(f)=X(f+f_0)
\end{align}
$$

## Time Scaling
$$x(at)\overset{\mathscr{F}}{\longleftrightarrow}\cfrac{1}{|a|}X\left(\cfrac{f}{a}\right)$$
#### Example
Perform a Fourier transform on $s(t)=\Pi_L(2t)$, where:
$$
\Pi_L(2t)=
\begin{cases}
1,&-\frac{L}{2}<2t<\frac{L}{2} \\
\\
0,& \text{elsewhere} \\
\end{cases}
$$
Becomes:
$$
\Pi_L(2t)=
\begin{cases}
1,&-\frac{L}{4}<t<\frac{L}{4} \\
\\
0,& \text{elsewhere} \\
\end{cases}
$$
![[Pasted image 20230817093933.png|centre|300]]
Given that: $\Pi_L(t)\longleftrightarrow Lsinc(fL)$ 
$$\Pi_L(2t)\overset{\mathscr{F}}{\longleftrightarrow}\frac{1}{2}L\space sinc\left(\frac{fL}{2}\right)

$$
## Time Reversal
$$x(-t)\overset{\mathscr{F}}{\longleftrightarrow}X(-f)$$
## Duality (symmetry)
$$X(-t)\overset{\mathscr{F}}{\longleftrightarrow}x(f)$$
$$X(t)\overset{\mathscr{F}}{\longleftrightarrow}x(-f)$$
##### Example

![[Pasted image 20230816214725.png]]





------
## Time Differentiation
$$\cfrac{d}{dt}x(t)\overset{\mathscr{F}}{\longleftrightarrow}j2\pi fX(f)$$
$n$th differentiation:
$$\cfrac{d^n}{dt^n}x(t)\overset{\mathscr{F}}{\longleftrightarrow}(j2\pi f)^nX(f)$$
## Frequency Differentiation
$$tx(t)\overset{\mathscr{F}}{\longleftrightarrow}\left(\cfrac{j}{2\pi}\right)\cfrac{d}{df}X(f) $$
$n$th differentiation:
$$t^nx(t)\overset{\mathscr{F}}{\longleftrightarrow}\left(\cfrac{j}{2\pi}\right)^n\cfrac{d^n}{df^n}X(f) $$

---- 

## Modulation
$$x(t)cos(2\pi f_0t)\overset{\mathscr{F}}{\longleftrightarrow}\frac{1}{2}[X(f-f_0)+X(f+f_0)]

$$

---

# Special Functions
## Gate Function
The gate (or rectangle) function is defined as:
$$
\Pi_T(t)=
\begin{cases}
1, \qquad -\frac{T}{2}\leq t\leq\frac{T}{2} \\
\\
0, \qquad \text{otherwise}
\end{cases}
$$
$$\Pi_T(t)=rect\left(\frac{t}{T}\right)\overset{\mathscr{F}}{\longleftrightarrow}Tsinc(Tf)=\cfrac{Tsin(\pi Tf)}{\pi Tf}$$
![[Pasted image 20230810133842.png|centre|200]]
## Unit Step Function
The unit step (or Heaviside) function is defined as:
$$
u(t)=
\begin{cases}
1, \qquad 1\geq 0 \\
\\
0, \qquad t<0
\end{cases}
$$
$$u(t)\overset{\mathscr{F}}{\longleftrightarrow}\frac{1}{2}\delta(f)+\frac{1}{j2\pi f}

$$
![[Pasted image 20230822202214.png|centre|200]]
## Dirac Delta Function
The Dirac delta (or impulse) function is defined as:
$$
\delta(t)=
\begin{cases}
0, \qquad t\neq0 \\
\\
\infty, \quad\space\space t=0
\end{cases}
$$
$$\int_{-\infty}^{\infty}\delta(t)\space dt=1$$
Likewise, the **shifted impulse** function can be defined as:
$$
\delta(t-t_0)=
\begin{cases}
0, \qquad t_0\neq0 \\
\\
\infty, \quad\space\space t_0=0
\end{cases}
$$
$$\int_{-\infty}^{\infty}\delta(t-t_0)\space dt=1$$
Therefore, we can infer the following shifting properties:
$$
\int_{-\infty}^{\infty}f(t)\space\delta(t-nt_0) \space dt= f(nt_0)
$$
Which produces the signal/function samples: $f(t_0),f(2t_0),f(3t_0),\dots,f(nt_0$ 

The Fourier transform:
$$\delta(t)\overset{\mathscr{F}}{\longleftrightarrow}1$$
$$\delta(t-t_0)\overset{\mathscr{F}}{\longleftrightarrow}e^{-j2\pi ft_0}$$
![[Pasted image 20230823232931.png|centre]]
