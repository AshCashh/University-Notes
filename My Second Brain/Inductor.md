#ee
Inductors create voltage to oppose a change in current. The ratio of voltage to the rate of change of current through an inductor is its inductance, measured in Henrys (H):
$$ v = L \frac{di}{dt} $$
 $$i(t) = \frac{1}{L}\int_0^t v(\tau)\space d\tau+ i(0){} $$
### Energy Stored 
$$W = \cfrac{1}{2}Li^2$$
### Steady State Conditions
When a circuit is in steady state, inductors can be modelled as short circuits.

## Inductors in Series and Parallel
Inductors in series and parallel operate in the same way as [[Resistor#Resistors in Series|resistors in series and parallel]].

### Inductors in Series
$$ L_1 + L_2 \dots = L_{eq}$$
### Inductors in Parallel
$$\cfrac{1}{L_1}+\cfrac{1}{L_2}\dots =\cfrac{1}{L_{eq}}$$
## Phasor Relationship
$$\mathbf{V}=j\omega L \mathbf{I}$$
Or in phasor form:
$$\mathbf{V}=I(\omega L\angle90\degree)$$
#### Example
![[Pasted image 20230430224728.png|300]]
Find the voltage across the inductor:
Current in phasor form: $\mathbf{I}=2\angle-45\degree mA$
Omega is: 1000

So:
$$\mathbf{V}=j\times1000\times5\times\mathbf{I}$$
in phasor form:
$$\mathbf{V}=\mathbf{I}(5000\angle90\degree)$$
sub in $\mathbf{I}$
$$\mathbf{V}=(2\angle-45\degree)mA(5000\angle90\degree)$$
$$\mathbf{V}=(2A\times5000mA\angle-45\degree+90\degree)$$
$$=(10\angle45\degree)$$
Rewrite:
$$V=10cos(1000t+45\degree)V$$
