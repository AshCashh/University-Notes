#ee
Step response also known as a forced response, is where the [[Circuit Elements|Circuit Element]] is driven by a [[Voltage Source]] or [[Current Source]]
![[Pasted image 20230416203651.png]]

![[Pasted image 20230416205234.png]]

## RC Step response
Before switch closes, cap voltage is $V_0$.
With switch closed we use KCL at top node:
$$ I_s = C\cfrac{dv}{dt} + \cfrac{v}{R}$$
We can separate and integrate to solve that
$$ v(t) = I_sR + (V_0 - I_sR)e^{-\cfrac{t}{RC}}, t > 0 $$
The voltage at t = $\tau$ is equal to:
$$ v(\tau) = (1-e^{-1})I_sR + V_0 = 0.632I_sR + V_0 $$
### Step Response problem
The capacitor in the circuit below is discharged. Find the voltage at 5 = 0.1s
![[Pasted image 20230416204306.png|200]]
Can do a Norton source transformation:
![[Pasted image 20230416204525.png|200]]
Then sub in:
$$ v(t) = 5+(0-5)e^{-\frac{0.1}{0.5}}$$
$$=0.91V$$

### Step Response of RL circuit
$$i(t) = \cfrac{V_s}{R}+(I_0-\cfrac{V_s}{R})e^{-\cfrac{R}{L}t}, t>0$$
The current at t = $\tau$ is equal to:
$$ i(\tau) = (1-e^{-1})\cfrac{V_s}{R}+ I_0$$
$$=0.632\cfrac{V_s}{R}+I_0$$


