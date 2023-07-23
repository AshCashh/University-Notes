#ee

Kirchhoff's circuit laws quantify how [[Current]] flows through a [[Circuit]] and how [[Voltage]] varies around a loop in a circuit.

There were first described in 1845 by German physicist Gustav Kirchhoff. Widely used in [[Electrical Engineering]], they are also called Kirchhoff's rules or simply Kirchhoff's laws. These laws can be applied in time and frequency domains and form the basis for network analysis.

## Current Law (KCL)
The current law states that the sum of all currents into a node equals zero.
![[Pasted image 20230519154302.png|centre|200]]
$$\sum i_{node} = 0$$
##### Current Law Examples
**How much current flows through the resistor?**
![[Pasted image 20230519154558.png|300]]
$$ i_1 + i_2 = i_3$$
$$ 10 + 5 = 15 A $$
**How much voltage across the resistor?**
$$ V = IR $$
$$ V = 15 \times{2} = 30 V $$
**Determine the values of the unknown currents:**
![[Pasted image 20230519155143.png|400]]
a)
$$ i_a = 1 + 3 = 4 $$
b)
$$ 3 + 1 + i_b - 2 = 0 $$
$$ i_b = -2 A $$
c)
$$ 1 + i_c + 4 + 3 = 0 $$
$$ i_c = -8 A $$



## Voltage Law (KVL)
The voltage law states that the sum of all voltages around a loop equals zero.
![[Pasted image 20230519154512.png|centre|200]]
$$\sum v_{loop} = 0$$

##### Voltage Law Examples

**What is the voltage across the resistor?**
$$ v_1 - v_2 - v_3 = 0 $$
$$ v_3 = v_1 - v_2 $$
$$ v_3 = 5 - 2 = 3V $$
**What is the current in the loop?**
$$ V = IR$$
$$ I = V/R $$
$$ I = 3/6 = 0.5 A $$

