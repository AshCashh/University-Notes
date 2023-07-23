#ee
A Rectifier is a [[Circuit]] that converts a [[Sinusoidal Signals|Sinusoidal Signal]] (AC) into a single-directional direct current (DC).

By using a [[Diodes|Diode]], a rectifier only allows [[Current]] to pass when an AC [[Voltage]] is positive, i.e. the diode donducts on the positive half cycle.
![[Pasted image 20230515133511.png]]

## Ripple Voltage
Ripple is the residual variation of the DC voltage after rectification. In the circuit shown above, a [[Capacitor]] can be used to smooth ripples.
![[Pasted image 20230515134223.png]]

Ripple can be calculated using the following assumptions:
1. The capacitor instantly charges when the diode is forward biased
2. The capacitor discharges with a constant current

The VI relationship for a capacitor gives the following formula for ripple:
$$\Delta v= \cfrac{i}{C}\Delta t=\cfrac{i}{fC}$$
## Half-wave Rectifier
![[Pasted image 20230515140335.png|centre|300]]
- The diode conducts on the positive half cycle
- The output loses the forward voltage of one diode

#### Half-wave Example
Choose a capacitor to keep the ripple voltage less than 0.1V
![[Pasted image 20230515134612.png|centre|300]]
To write the voltage as a function of time we use ([[Root Mean Square#RMS Voltage:]])
$$v(t)= 5\sqrt{2}cos(100\pi t)$$
When positively conducting there will be a drop across the diode, assuming a drop of 0.7V: $v_{out}=5\sqrt{2}-0.7\approx 6.3$ 

Rearrange ripple formula for C:
$$C=\cfrac{i}{\Delta vf}$$
Since we're looking for the capacitor to keep the ripple voltage less than 0.1, it becomes:
$$C>\cfrac{i}{\Delta vf}$$
Current:
$$i=\cfrac{6.3}{100}=63mA$$
So:
$$\therefore C>\cfrac{0.063}{0.1\times50}$$
$$C>12.6mF$$



## Full-wave Rectifier
![[Pasted image 20230515140502.png|centre|300]]
- Two diodes conduct every half cycle
- The output loses the forward voltage of two diodes

The ripple voltage in a full-wave rectifier is calculated using
$$\Delta v=\cfrac{i}{2fC}$$
## Dual Half-wave Rectifier
![[Pasted image 20230515140946.png|centre|300]]
- The diodes conduct on both cycles
- The output loses the forward voltage of one diode
- Useful for powering op amps

The ripple in a dual half-wave rectifier is calulcated using
$$\Delta v=\cfrac{i}{fC}$$

### Power Supply Design
Design a power supply to provide 5V @ 100mA from a 12 VAC RMS 50Hz plugpack.

Peak voltage:
$$v_{peak}=\sqrt{2}\times12\approx17V$$
Minimum voltage:
$$v_{min}=5+2=7V$$
Maximum ripple: $17-7=10V$

Using the ripple voltage formula we can find C:
$$C>\cfrac{0.1}{50\times10}$$
$$C>200\mu F$$
