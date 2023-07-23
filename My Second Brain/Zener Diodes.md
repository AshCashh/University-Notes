#ee
A Zener diode is similar to a regular [[Diodes|Diode]], but it has a specific reverse breakdown [[Voltage]]. The reverse breakdown voltage ($v_r$)is commonly 5V. 
![[Pasted image 20230521165600.png|centre|300]]
The ideal VI characteristic for a Zener diode is shown below,
![[Pasted image 20230521165815.png|centre|200]]
##### Zener Regulator Example
Find the voltage $v$ across the Zener diode for $v_s=6V$ and then for 12V
![[Pasted image 20230521165928.png|300]]
Supplied more than 5V to the Zener diode, therefore the diode must be in its reverse breakdown mode. Therefore, the voltage across the diode must be 5V in both situations.

Find the current $i$ through the diode for each case ($v_s = 6V$ and $v_s=12V$)

Using KVL:
$$V_d+iR+V_s = 0$$
When $v_s = 6$:
$$-5 + i\times 10 + 6 = 0$$
$$i = -0.1A$$
When $v_s  = 12$:
$$-5 + i\times 10 +12=0$$
$$i=-0.7A$$
Find the power dissipated by the diode for each case:

$$P=VI$$
For $v_s = 6$:
$$= -5\times-0.1=0.5W$$
For $v_s = 12$:
$$=-5\times -0.7=3.5W$$
#### Effect of a Load
Consider the voltage regulator with a 6V input and a $1\ohm$ load.
Will the voltage across the load resistor be 5V?
![[Pasted image 20230521171432.png|300]]

If there was 5V across the load, there would be 5A through the load. That would mean a 50V drop across the $10\ohm$ resistor. If the diode is not conducting, the circuit becomes:
![[Pasted image 20230521172001.png|200]]

#### Maximum Current
Find the maximum current $i_L$ that the ideal diode can regulate
![[Pasted image 20230521172043.png|300]]
$$i_sR_s < v_s-v_z$$
For a small $i_z$, $i_s\approx i_L$:
$$\therefore i_LR_s < v_s-v_z$$
$$i_L < \cfrac{v_s-v_z}{R_s}$$
$$i_L < 100mA$$
If this load current goes above 100mA, the diode wont be regulating and end up with what happened in [[Zener Diodes#Effect of a Load| Effect of a Load]]






