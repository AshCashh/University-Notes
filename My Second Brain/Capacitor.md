#ee
Capacitors store electrical energy as a voltage. The ratio of voltage to charge across a capacitor is its capacitance, measured in Farads (F):
$$q = Cv$$
$$ v(t) = \frac{1}{C}\int_0^t idf + v(0){} $$

A 1 Farad capacitor is connected to a 10 A current source. What will be the rate of voltage rise across the capacitor?
$$ \frac{dv}{dt} = \frac{i}{C} = \frac{10A}{1F} = 10 V/s$$

A discharged 100 uF capacitor is connected to a 1mA current source at 8:00 am. What voltage will te capacitor reach by 9:00 am?
$$ v(3600) = \frac{1}{100\times10^{-6}}\int_0^{3600} 0.001 df + 0 $$
$$ 10000 \times 0.001\times 3600 = 36000 V $$
## Capacitors in Series and Parallel
Inductors in series and parallel operate in the opposite way as [[Resistor#Resistors in Series|resistors in series and parallel]].

### Capacitors in series
$$\cfrac{1}{C_1}+\cfrac{1}{C_2}\dots =\cfrac{1}{C_{eq}}$$

### Capacitors in parallel
$$C_1 + C_2 + \dots = C_{eq}$$
## Phasor Relationship
$$\mathbf{V}=\cfrac{1}{j\omega C}\mathbf{I}$$
Or in phasor form:
$$\mathbf{V}=\mathbf{I}\left(\cfrac{1}{\omega C}\angle-90\degree\right)$$

#### Example
![[Pasted image 20230430230617.png|200]]
Find the RMS current through the capacitor
Phasor form: $339\angle0\degree$
Rearrangle capacitor formula for current:
$$\mathbf{I}=\cfrac{V}{\cfrac{1}{\omega C}\angle-90\degree}$$
Sub in $v(t)$:
$$\mathbf{I}=\cfrac{339\angle0\degree}{\cfrac{1}{100\pi \times 1\times10^{-6}}\angle-90\degree}$$
$$\mathbf{I}=\cfrac{339\angle0\degree}{3138 C\angle-90\degree}$$
$$=107\angle90\degree mA$$
Finding RMS current:
$$I_{RMS}=\cfrac{I_m}{\sqrt{2}}=\cfrac{107}{\sqrt{2}}=75.7mA$$
