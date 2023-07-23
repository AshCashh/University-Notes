#ee
Power (p) is the rate of change of [[Energy]] over time, measured in Watts (W) or joules per second. 
$$p=\frac{dw}{dt}=1W=1\frac{J}{s}$$
Electric power is the product of [[Voltage]] and [[Current]] and can be determined through the equation:
$$ p = vi$$
Power is the rate that the bucket of water is filling for a given height.
![[Pasted image 20230629060210.png|400]]

## Sign Convention
Positive power means that power is being dissipated (used) by the element
![[Pasted image 20230629060249.png]]
Works in opposite. Where energy is being produced, and therefore has a negative power value.

## Power Transfer
- When elements are connected, power transfers from one element to the other.
- In this case, element A is delivering power and element B is extracting power.
- Power is transferred from A to B
![[Pasted image 20230629060554.png|300]]
- Power is transferred from B to A
![[Pasted image 20230629060730.png|300]]

## Power Balance
- With multiple elements in a circuit, we expect the power to balance to zero.
- Verify that the power balances to zero in this circuit by calculating the power produced or dissipated by each element.

## Maximum Power Transfer
In the circuit below, the maximum power transfer to the load is given by:
$$ P_L = \frac{v^2_{Th}}{4R_L}$$
where $R_L=R_{Th}$
![[Pasted image 20230326173247.png|centre|400]]
##### Example:
Find the value of $R_L$ to maximise power transfer.
![[Pasted image 20230326173436.png|300]]
First find $v_{Th}$ Use [[Superposition]]
Open circuit the current source:
![[Pasted image 20230326174029.png|300]]
Using a voltage divider:
$$ V_{Th}' = 6 \times \frac{2}{2+3+1}$$
$$ = 2V$$
Closed circuit the voltage source
![[Pasted image 20230326174323.png]]
$$ V_{Th}''= 2 \times 4\ohm || 2\ohm$$
$$= \frac{8}{3}V$$
Therefore:
$$V_{Th} = 2V + \frac{8}{3}V = \frac{14}{3} $$
Now find $R_{Th}$. Set both sources to 0
![[Pasted image 20230326174900.png|200]]
$R_{Th} = 4\ohm || 2\ohm = \cfrac{4}{3}\ohm$

Now to find the max power transfer use formula. Remembering $R_L = R_{Th}$ and $V_{Th} = \frac{14}{3}, R_L = \frac{4}{3}$
Therefore,
$$ P_L = \cfrac{(14/3)^2}{4(4/3)} = \frac{49}{12}W$$
