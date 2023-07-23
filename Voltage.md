#ee
Voltage (*v*), also known as electric pressure, electric tension or the *electrical potential difference* between two points in a [[Circuit]], measured in Volts (V).
- Voltage is measured across a [[Circuit Elements|Circuit Element]] or between two points in a [[Circuit]], commonly with respect to a 0 V reference (GND). 
- It represents the potential of the electrical system to do [[Work]].
- One Volt is defined as energy consumption of one joule per flectric charge of one coulomb. $1V = 1J/C$
- One Volt is equal to the current of 1 amp times the resistance of 1 ohm

Think of voltage as the height of the bucket of water above the pool

## Voltage Divider
A simple circuit that divides a voltage in the proportion of the [[Resistor#Resistors in Series]] 
![[Pasted image 20230306083137.png|200]]
The [[Current]] through the resistors is:
$$ i = \cfrac{v}{R_1+R_2} $$
The voltage across the resistors using [[Ohm's Law]]
$$ v_1 = iR_1; v_2 = iR_2 $$
$$ v_1 = v\cfrac{R_1}{R_1+R_2}; v_2=v\cfrac{R_2}{R_1+R_2} $$
For more resistors:
$$ v_j = v\cfrac{R_j}{R_{eq}} $$
Where $v_j$ is the voltage of resistor and $v$ is the voltage of the circuit.
##### DC Voltage Divider Example:
![[Pasted image 20230306083659.png|200]]
Find the voltage across the $15 \ohm$ resistor.
Using 
$$v_1 = v\cfrac{R_1}{R_1+R_2}$$
$$v_1 = 5\cfrac{15000}{15000+10000} $$
$$v_1 = \cfrac{75000}{25000} = 3V $$

##### AC Voltage Divider Example:
Find the voltage across the resistor:
![[Pasted image 20230508143951.png|400]]
Express voltage as phasor and passive elements as complex numbers

Voltage source: $10\angle0\degree$
Inductor: $j5000\times2\times10^{-3}=j10$ Phasor: $10\angle90\degree\ohm$
Resistor: $5\ohm$
Capacitor: $\cfrac{1}{j5000\times100\times10^{-6}}=\cfrac{1}{j0.5}=-j2\ohm$

Combine the impedance using series and parallel formulae.
![[Pasted image 20230508144627.png|200]]
$$\mathbf{Z}_{parallel}=\cfrac{1}{\cfrac{1}{10j}+\cfrac{1}{-2j}}=\cfrac{1}{-0.1j+0.5j}=\cfrac{1}{0.4j}=-2.5j\ohm$$
$$\mathbf{Z}_{series}=5-2.5j$$
In phasor form:

Magnitude:
$$V_m=\sqrt{5^2+(-2.5)^2}=5.59$$
Angle:
$$\phi=-tan^{-1}\left(\cfrac{2.5}{5}\right)=-27\degree$$
Phasor is:
$$5.58\angle-27\degree$$
Using voltage divider formula:
$$V_R=V_s\cfrac{\mathbf{Z}_R}{\mathbf{Z}_I+\mathbf{Z}_C}=10\angle0\degree\times\cfrac{5\angle0\degree}{5.58\angle-27\degree}=\cfrac{50\angle0\degree}{5.58\angle-27\degree}=8.96\angle27\degree$$
## Measuring Voltage
A voltmeter measures voltage between two points. The voltmeter has very high resistance, so it doesnt affect the circuit