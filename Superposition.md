#ee
[[Thevenin Equivalent|Thevenin's Theorem]]: Any linear circuit can be replaced by a [[Voltage Source]] and a [[Resistor#Resistors in Series|resistor in series]].

[[Norton Equivalent Circuits|Norton's Theorem]]: Any linear circuit can be replaced by a [[Current Source]] and a [[Resistor#Resistors in Parallel|resistor in parallel]].

Turning a sources "off" means to set its value to 0:
For a voltage source $v = 0V$, hence we can treat it as a [[Short Circuit]]
For a current source $i=0A$, hence we can treat it as an [[Open Circuit]]

##### Example:
Find voltage at node a by superposition.
First find contribution from voltage source (open circuit the current source)
![[Pasted image 20230326164224.png|300]]
Voltage from a using voltage divider formula:
![[Pasted image 20230326164400.png|400]]
Now find contribution from current source (short circuit the voltage source). Using current divider:
![[Pasted image 20230326164739.png|400]]
Contribution from voltage source. $v_a' = 10/3V$
Contribution from current source. $v_a'' = 4/3V$
Therefore: $v_a=v_a' + v_a'' = 14/3$

Now to find $R_{Th}$ we use Thevenin Theorems
Set all sources to 0.

