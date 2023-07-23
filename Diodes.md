#ee
The diode is a basic but very important [[Circuit Elements|Circuit Element]] that has two terminals, the anode and the cathode. Current flows in the direction of the arrow and, not against. The symbol for the diode is shown below,
![[Pasted image 20230311132502.png]]
- When $v_d >$ forward voltage, the diode is forward biased, and therefore $i_d >$ 0
- When $v_d < 0$, the diode is reverse biased, and therefore $i_d \approx 0$

## Simplified Characteristics
- The diode has non-linear characteristics
- This is the simplified version: calculations are easier, but results are less accurate
![[Pasted image 20230311142616.png|200]]

## Full Characteristic 
- The diode can be better modelled using Shockley's equation. In it's simplest form:
$$ i_D = I_S * exp\left(\cfrac{v_D}{V_T} \right)$$
Where $I_S$ is Saturation current and $V_T$ is the Thermal voltage (26mV / 0.026 V)
![[Pasted image 20230311155831.png|300]]

## Finding the Saturation Current
A diode is known to have 0.9V forward voltage at 1A
Find the diodes saturation current:
$$ 1 = I_S*exp\left(\frac{0.9}{0.026}\right)$$
Rearrange for $I_S$
$$ I_S = \cfrac{1}{1.08*10^{15}} = 9.2*10^{-16}$$
##### Diode Problem
A diode has 0.62 V forward voltage at 5mA forward current.
![[Pasted image 20230311175021.png|200]]
Find the power dissipated by the diode in this circuit.
Use the simple model first.
Use the full model next.

Simple Model Solution:

Using KVL,
$1-10i-0.62$
Rearrange: $i = 38mA$
Power: $P = VI = 0.62\times 38 = 24mW$

Or using a [[Operating Points#Load Line]]
Sketch:
![[Pasted image 20230311175419.png|300]]

Full Model solution:
![[Pasted image 20230311175550.png|300]]