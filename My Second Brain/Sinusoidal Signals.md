#ee
A sinusoidal signal is commonly referred to as Alternating Current (AC).
![[Pasted image 20230508110922.png|centre|400]]
We can describe the signal with a cosine function:
$$ v(t) = V_mcos(\omega t+ \phi)$$
where $\omega$ is angular frequency, $V_m$ is magnitude and $\phi$ is phase.

### Magnitude ($V_m$)
The magnitude of a signal is the greatest distance from the line of oscillation, commonly zero, to the peak of the signal. It defines the units, i.e. $V_m = 1V$

### Angular Frequency ($\omega$)
The angular frequency is in radians per second and allows us to compete the cosine function in radians.

### Period and Frequency 
The period is the cycle time, $T$ in seconds (s).
The frequency is cycles per second or the inverse of period, $f$ in Hertz (Hz).

The following equations relate the angular frequency, period and frequency together:
$$f=\cfrac{1}{T},\phantom{AAA} T=\cfrac{2\pi}{\omega}, \phantom{AAA} \omega = 2\pi f=\cfrac{2\pi}{T} $$

### Phase ($\phi$)
The phase of a signal is the position of a signal relative to a zero phase signal, measured in degrees ($\degree$). A positive phase corresponds to a "leading" signal, and a negative phase corresponds to a "lagging" signal. The phase can be determined by calculating the difference in time $\tau$ between two signals 
$$ \phi = \cfrac{\tau}{T}\times360\degree$$
#### Positive Phase Example
![[Pasted image 20230430150939.png|400]]
- Red dashed signal has phase of 0 degrees
- Blue signal is ahead in time
Difference $\tau$ is 0.16 seconds
Phase is:
$$\phi = \cfrac{0.16}{1} \times 360\degree = 60\degree$$


#### Negative Phase Example
![[Pasted image 20230430151144.png|400]]
- Red dashed signal has phase of 0 degrees
- Blue signal is a delayed version
Time difference $\tau$ is 0.25 seconds
Phase is: 
$$\phi = \cfrac{-0.25}{1} \times 360\degree = -90\degree $$
#### Sinusoidal Signal Quiz
![[Pasted image 20230430151444.png|400]]
Magnitude $V_m$:
$$ V_m = 80V$$
Angular Frequency $\omega$
$$\omega = \cfrac{2\pi}{T}=\cfrac{2\pi}{0.04}=50\pi \phantom{A}rad/s$$
Phase $\phi$:
$$\phi = \cfrac{\tau}{T}\times 360\degree = \cfrac{0.005}{0.04}\times 360\degree = 45\degree$$
Signal v:
$$ v = V_mcos(\omega t+ \phi)= 80(50\pi t+ 45\degree)$$