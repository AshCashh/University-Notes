#ee
Most circuits require a clean DC power supply to operate. A [[Voltage]] regulator ensures that a DC power supply behaves like an ideal [[Voltage Source]] (stable voltage, no matter the current). 

# Shunt Regulators
A shunt regulator regulates the output voltage by shunning excess current away from the load. A [[Zener Diodes|Zener Diode]] (specifically a Zener Regulator) can be used as a shunt regulator to drop voltages to the reverse bias voltage of the diode (Commonly 5V).

When designing a Zener voltage regulator, the following should be taken into account:
- [[Power]] dissipation particularly when dropping large voltages
- Large [[Resistor#Resistors in Series|series resistances]] reduces power dissipation but also reduces the regulated current
- A Zener voltage regulator always draws power from the source, regardless of the load
- The load has an effect on the regulator
![[Pasted image 20230521175045.png|centre|300]]
## Maximum Load Current
Given a source voltage range $v_s$ and a source resistance $R_s$, the maximum current an ideal Zener diode can regulate is given by:
$$i_L < \cfrac{v_s-v_z}{R_s}$$
where the largest value in $v_s$ is chosen.

## Maximum Source Resistance
Given a source voltage range $v_s$ and load current range $i_L$, the maximum source resistance required to regulate the output voltage is given by:
$$R_s<\cfrac{v_s-v_z}{i_L}$$
where the smallest value in $v_s$ is chosen, and the largest value in $i_L$ is chosen.

# Series Regulators
Series regulators regulate the output voltage by limiting the load current by varying the series element.

## Series Linear Regulators
LM-series [[Integrated Circuits]] are a three-terminal linear regulator that regulate fixed voltages of 0.5V to 24V. They require an input voltage at least 2V greater than the regulated output voltage. The capacitors remain the same forany output voltage.
![[Pasted image 20230521180647.png]]

The naming convention is as follows,
1. LM78XX regulates a positive voltage of XX (LM7805 = 5V)
2. LM79XX regulates a negative voltage of XX (LM7905 = -5V)

### Power Dissipation
How much power will be dissipated by the regulator?
![[Pasted image 20230521184847.png|300]]

Input current = output current. The output current equals:
$$I=\cfrac{5}{10}=0.5A$$
$v_i = 12V$, $v_o=5V$. So the voltage dissipated must be: 
$$V=12-5=7V$$
Therefore the power dissipated by the regulator is:
$$P=VI=7\times0.5=3.5W$$
## Op-Amps as a Regulator
[[Operational Amplifiers]] can be utilised to stabilise the output from a regulator. The op amp is powered by the source voltage and the series resistance is chosen to minimise the current through the Zender diode.
![[Pasted image 20230521210923.png|centre|400]]
In the cirucit above, $i_Z + i_S = 0$

The power dissipated by the cirucit can be determined by finding the power produced at the voltage source which is given by:
$$p=v_{in}(i_L-i_Z)$$
#### Example Op-amp as a regulator
What is the voltage across $R_L$?
![[Pasted image 20230521211430.png]]
Since the Op amp is a[[Operational Amplifiers#Voltage Follower / Voltage Buffer| Voltage Follower]], $v_{in}=v_{out}$

So knowing that $v_Z = 5V$:
$$v_Z=v_{in}=v_{out}=v_L = 5V$$

#### Example 2 
![[Pasted image 20230521212106.png]]

What base op-amp circuit does this regulator use?
A [[Operational Amplifiers#Non-Inverting Amplifier|Non-Inverting]] amplifier.

What resistor value will set $v_{out} = 5V$?

If $v_{out}=5V$:
$$v_{out}=\left(1+\cfrac{R_2}{R_1}\right)v_n$$
$$5=\left(1+\cfrac{R_2}{10000}\right)1.25$$
$$R_2=30000\ohm$$
