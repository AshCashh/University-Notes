#ee
Current (i) is the rate of flow of electrical [[Charge]] through a [[Circuit]] / the amount of electrcity flowing through a circuit, measured in Amperes (A).
- Current is measured through a [[Circuit Elements|Circuit Element]].
- Amps are Coulombs per second
- The larger the value in amperes, the more [[Electricity]] is flowing in the circuit.

Think of current as the rate of water flow.

## Current Divider 
A simple circuit that divides current between [[Resistor#Resistors in Parallel|Resistors in Parallel]]
![[Pasted image 20230306085208.png|300]]
The [[Voltage]] across the resistors is:
$$ v= i\left(R_1\parallel R_2\parallel R_3\right)$$
The current through each resistor:
$$ i_j = \cfrac{v}{R_j} $$
$$ = i\cfrac{\left(R_1\parallel R_2\parallel R_3\right)}{R_j} $$
For more resistors:
$$ i_j = i\frac{R_{eq}}{R_j} $$
##### Example:
```start-multi-column  
ID: ExampleRegion1  
number of columns: 2  
number of rows: 2
largest column: middle  
```

![[Pasted image 20230306090109.png|300]]

--- end-column ---

Using,
$$  i_j = i\frac{R_{eq}}{R_j}  $$
Finding $R_{eq}$ using [[Resistor#Resistors in Parallel]]
$$ R_{eq} = \frac{1}{\cfrac{1}{10}+\cfrac{1}{10}+\cfrac{1}{5}} = 2.5\ohm$$
Therefore,

$$ i_j = 1\frac{2.5}{5}  = 0.5A$$


=== end-multi-column
## Measuring Current
An ammeter measures current through a wire. The ammeter has very low resistance, so it doesnt affect the circuit. The curcuit must be broken to measure current.