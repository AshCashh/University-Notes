#ee
A natural response is a decaying response for a [[Resistor]]-[[Capacitor]] and resistor-[[Inductor]] [[Circuit]]

![[Pasted image 20230416205248.png]]

## Switched RC Circuit
Assume that the switch has been in the first position for a long to find initial condition
What is the voltage just before t = 0?
![[Pasted image 20230416191348.png]]

### Initial Condition
Perform stead state analysis
- Treat capacitor as open circuit
![[Pasted image 20230416191448.png]]
Just before t = 0, voltage across the capacitor is the same as the voltage source Vs

## Intuitive Response of RC circuit
As current leaves capacitor, voltage will fall.
As v(t) falls, the current $i(t) = \cfrac{v(t)}{R_2}$ will fall.
Eventually the capacitor will discharge and the current will stop.
![[Pasted image 20230416191818.png]]

## Natural Response of RC circuit
We can use KCL to get:
$$ -C\cfrac{dv}{dt} = \cfrac{v}{R_2}$$
We can find a solution by separating and integrating.
![[Pasted image 20230416191922.png|300]]

$$v(t) = v(0)e^{-\cfrac{t}{RC}}$$
where $\tau = RC$ is called the time constant
![[Pasted image 20230416192503.png|400]]
The voltage at this time is equal to $e^{-1)}v(0) = 0.3.68v(0)$

For the circuit below,
![Pasted image 20230416193119.png](app://local/Users/ashasaunders/Documents/Uni/Engineering%20&%20IT/PNGs/Pasted%20image%2020230416193119.png?1681637479813)

Using mesh analysis gives the following relationship:
$$ L\cfrac{di}{dt} = -iR$$
By solving this differential equation, we can determine the natural response:
$$ i(t) = i(0)e^{-\cfrac{R_2}{L}t}$$
where $\tau = \cfrac{L}{R}$ is the time constant.

### RC Problem Example
Given that the switch has been in the first positon for a long time, find v when t = 200ms.
![[Pasted image 20230416192552.png|200]]
First steady state: Vs = Vc = V(0) = 10v
Then substitute v(0) = 10v into the natural response formula:
$$ V(t) = 10e^{-\cfrac{t}{1\times 10^3 \times 100\times 10^-6}}$$
$$=10e^{-10t}v$$
then sub t = 200ms:
$$ V(200ms) = V(0.2) = 10e^{-10\times0.2} = 1.35V$$

#### Another example with inductors
What is the current just before t = 0
![[Pasted image 20230416193119.png]]
First stead state analysis (treat inductor as short circuit):
![[Pasted image 20230416193259.png|300]]
Just before t = 0, current through the inductor is the same as the current source Is. Therefore, $I = I_s$


### RL Problem
Given that the switch has been in the first position for a long time, find the current when t = 2ms
![[Pasted image 20230416202621.png|300]]
First find initial current time:
$$i(0) = \frac{10}{5} = 2A$$
Sub into RL formula:
$$ i(t) = 2e^{-\cfrac{10}{10\times10^{-3}}t}$$
$$=2e^{-1000t}A$$
Therefore,
$$i(2ms) = i(2\times10^{-3}) = 2e^{-2} = 0.27A$$