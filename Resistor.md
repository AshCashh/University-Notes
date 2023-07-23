#ee
A resistor is a [[Circuit Elements|Circuit Element]] that dissipates [[Power]] with a specified ratio between [[Voltage]] and [[Current]], known as [[Resistance]].
![[Pasted image 20230305202642.png|100]]
Ratio of voltage to current is constant: $\cfrac{v}{i}=constant$
![[Pasted image 20230305202802.png|100]]
The restriction in the pipe restricts the rate of flow of water depending on the amount of pressure drop.

## Characteristics
![[Pasted image 20230311141351.png|200]]
Rearranging [[Ohm's Law]] we get
$$ I = \frac{V}{R}$$
Therefore the gradient of a voltage-current graph is: $\cfrac{1}{R}$
##### Example:
Add values to the i axis and plot the V-I characteristic curve for a $10\ohm$ resistor
Using,
$$ I = \frac{1}{R} V $$
![[Pasted image 20230311142450.png|200]]


## Resistors Always Dissipate Power
![[Pasted image 20230305204337.png|200]]
- Charge is moving from high energy to low energy
- Resistor is dissipating power (positive power)
![[Pasted image 20230305204421.png|200]]
- Charge is moving from low energy to high energy
- Resistor is creating power (negative power)

## Power in a resistor
There are three main formulas you can use to calculate the power in a resistor.

Known Voltage/Current
$$p = v*i$$
Unknown Current:
$$ p = \frac{v^2}{R}$$
Unknown Voltage
$$ p = i^2R$$
Note: $v$ and $i$ is in terms of the resistor not the source.

## Resistors in Series
The total resistance in a [[Series Circuits|Series Circuit]] is equivalent to the sum of the individual resistors, given by:
![200](app://local/Users/ashasaunders/Downloads/ash's%20vault/Pasted%20image%2020230305154814.png?1677995294050)
$$ R_{series} = \sum_{i}R_i = R_1 + R_2 + \dots + R_k $$
##### Example:
![200](app://local/Users/ashasaunders/Downloads/ash's%20vault/Pasted%20image%2020230305151006.png?1677993006982)
Current is the same in all resistors, i.e. $i_1 = i_2 = i_3 = i$
KVL gives:
$$ v-iR_1 - iR_2 - iR_3 = 0 $$
$$ v = i(R_1 + R_2 + R_3)$$
Equivalent resistance: 
$$ R_{eq} = R_1 + R_2 + R_3 $$
Therefore, **resistors in series are summed**

## Resistors in Parallel
The inverse resistance in a [[Parallel Circuits|Parallel Circuit]] is equivalent to the sum of the inverse of parallel resistances, given by:
![300](app://local/Users/ashasaunders/Downloads/ash's%20vault/Pasted%20image%2020230305155209.png?1677995529523)
$$ \frac{1}{R_{parallel}} = \sum_{i}\frac{1}{R_i}=\frac{1}{R_1}+\frac{1}{R_2}+\dots+\frac{1}{R_k} $$
$$ R_{parallel} = \frac{1}{\cfrac{1}{R_1}+\cfrac{1}{R_2}+\dots+\cfrac{1}{R_k}}$$
Or (with two resistors)
$$R_{parallel} = \cfrac{R_1\times R_2}{R_1+R_2}$$


##### Example:
![200](app://local/Users/ashasaunders/Downloads/ash's%20vault/Pasted%20image%2020230305153438.png?1677994478594)
The voltage across the rsistors are the same
$$ v = i_iR_i=i_2R_2=i_3R_3 $$
Therefore:
$$ i_1 = \frac{v}{R_1};i_2=\frac{v}{R_2};i_3=\frac{v}{R_3}$$
$$i = v\left(\frac{1}{R_1}+\frac{1}{R_2}+\frac{1}{R_3}\right) $$
$$ \frac{i}{v} = \frac{1}{R_{eq}} = \frac{1}{R_1}+\frac{1}{R_2}+\frac{1}{R_3}$$
## [[Phasors|Phasor]] Relationship 
From [[Ohm's Law]]:
$$ \mathbf{V} = \mathbf{I}R$$
##### Proof:
Using a sinusoidal voltage:
$$v=V_mcos(\omega t+\phi)$$
Ohm's Law gives: $i=\cfrac{v}{R}$
$$=\cfrac{V_m}{R}cos(\omega t+\phi)$$
Taking the Phasor Transform gives:
$$
\mathscr{P}\{v\}=\mathscr{P}\{iR\}

$$
$$\mathscr{P}\left \{V_mcos(\omega t+\phi)\right \}=\mathscr{P}\left \{\frac{V_m}{R}cos(\omega t + \phi\right \}R$$
$$\mathbf{V}=\mathbf{I}R$$



#### Example
![[Pasted image 20230430221232.png|300]]
Find the voltage across the resistor:
Write current in phasor form:
$$I=2\angle45\degree mA$$
$$\mathbf{V}=(2\angle45\degree)2 = 4\angle45\degree V$$
Rewrite:
$$\mathbf{V}=4cos(\omega t+45\degree)V$$
