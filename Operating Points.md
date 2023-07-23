#ee
If you have a [[Voltage]]-[[Current]] characteristic for two elements you can find the operating point when those two elements are connected together.
![[Pasted image 20230311160752.png|300]]

##### Example:
Draw a plot that shows the operating point for this circuit
![[Pasted image 20230311160823.png|200]]
$V = 20$
$I = \frac{1}{R}\times V = 2$
![[Pasted image 20230311161115.png|200]]

Find the operating point for this circuit. Assume a simple diode with forward voltage of 0.7 V
![[Pasted image 20230311161203.png|200]]
Current souce: 20mA
Diode: Forward voltage at 0.7 V
![[Pasted image 20230311161418.png|200]]

Find the operating point for this circuit. Assume a simple diode with forward voltage of 0.7 V
![[Pasted image 20230311161503.png|200]]
Current source: -20ma
Diode: Forward voltage at 0.7 V

Elements dont interact.


## Load Line
When dealing with three or more [[Circuit Elements]] including a diode a load line must be found.

A load line shows a range of voltage and current values for a particular element. This is done by considering the two extremes in the circuit (short circuit and open circuit) and drawing a line between these two points.

Once the load line is established, you can then find the operating point by adding the diode to the V-I graph.

##### Example:
![[Pasted image 20230311171821.png|200]]
Look at the circuit in two parts:
1. Short circuit:
First replace the diode with a straight wire.	 
![[Pasted image 20230311172053.png|200]]
- Find the current if we went through that short circuit and plot
![[Pasted image 20230311172306.png|200]]
$I = 2/20 = 100mA$
Theres no component so the voltage is 0

2. Open circuit
When the diode is removed (so theres a hole in the circuit, current is 0)
The voltage therefore must be 2 V.
Draw a line between the two extremes (the load line).

Now you could use KVL as before:
$2=20i+0.7$
Rearrange: $i=65mA$
![[Pasted image 20230311174354.png|200]]


##### Load Line Problem
Draw a load line for this circuit.
![[Pasted image 20230311173444.png|200]]
1. Short circuit:
Voltage = 0
Current:   $i_{sc} =\cfrac{5}{100} = 0.05A$ or 50 mA

2. Open circuit
Current = 0
Voltage = 5
![[Pasted image 20230311173946.png|200]]


