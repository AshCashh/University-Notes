#ee
Similar to the [[Thevenin Equivalent]] model, we can use a [[Current Source]] with a [[Resistor#Resistors in Parallel|Resistor in parallel]] to model the same circuit.
![[Pasted image 20230323155426.png|centre|300]]
This circuit has the following properties:
Open circuit voltage:
$$ v_{oc} = i_{sc}R_p$$
Short circuit current:
$$ i_{sc} = i_{sc} $$
$$\therefore i_{sc} = \frac{v_{Th}}{R_{Th}} $$
The relationship between Thevenin and Norton equivalent circuits have the following relationship:
$$ R_{Th} = R_p $$
##### Example:
Find the Norton equivalent for a 9V battery:
![[Pasted image 20230323160313.png|200]]
Using $i_{sc} = \frac{v_{oc}}{R_{Th}}$:
$$ \frac{9}{2.27} = 3.97A$$
![[Pasted image 20230323160632.png|300]]
