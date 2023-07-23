#ee
Electronic filters are a type of [[Signal Processing]] filter in the form of electronic [[Circuit|Circuits]] designed to allow certain ranges of [[Frequency|Frequencies]] to pass, while other ranges of frequencies are stopped.

## Ideal Filters
![[Pasted image 20230514002912.png]]

### Low Pass Example
[[Frequency Response#Frequency Response Example]]
What will $H(\omega)$ be for 10Hz and 10kHz:
$$\omega_1=20\pi, \omega_2=20k\pi$$
Sub into [[Transfer Function]]:
$$H(\omega_1)=\cfrac{1000}{j\times20\pi+1000}=1\angle 0\degree$$
$$H(\omega_2)=\cfrac{1000}{j\times20k\pi+1000}=0.016\angle -90\degree$$
Plotting the Response we get:
![[Pasted image 20230515004316.png]]


## Passive Filters
Passive filters are circuits containing only passive elements (such as [[Resistor|Resistors]], [[Capacitor|Capacitors]] and [[Inductor|Inductors]])
![[Pasted image 20230515121338.png]]

### Low Pass Filter
The following low pass filter has the following transfer function
$$\mathbf{H}(\omega)=\cfrac{\omega_c}{j\omega+\omega_c}$$
where $\omega_c = \cfrac{1}{RC}$
![[Pasted image 20230515005207.png|centre|300]]

### High Pass Filter
The following high pass filter has the following transfer function
$$\mathbf{H}(\omega)=\cfrac{j\omega}{j\omega+\omega_c}$$
where $\omega_c = \cfrac{1}{RC}$
![[Pasted image 20230515005402.png|centre|300]]

#### Designing a High Pass Filter
Design a high-pass filter to remove audio rumble below 20Hz

Cut-off frequency: $f_c=20Hz$ 
Convert to rad/s: $\omega_c=2\pi\times f_c=40\pi$
$\therefore 40\pi=\cfrac{1}{RC}$

Picking a capacitor, choose $C=10\mu F$ 
Resistance: $R=\cfrac{1}{40\pi\times10\times10^{-6}}=796\ohm$

What happens when I connect a speaker with resistance of 8$\ohm$. Find the new $\omega_c$
![[Pasted image 20230515010118.png|200]]

$$R_{eq}=\cfrac{8\times796}{8+796}=7.92\ohm$$
$$\therefore \omega_c=\cfrac{1}{7.92\times10\times10^{-6}}=2kHz$$
This is a problem because the speaker is affecting the audio rumble thats suppose to be below 20Hz. Therefore an active filter should be considered



## Active Filters
Active filters are circuits containing active elements (such as [[Operational Amplifiers]]), which filter unwanted parts of a signal. Active filters are not affected by loading such that a varied load will not affect the cut-off frequency.

For the following active filters, the gain component is given by:
$$gain=-\cfrac{R_2}{R_1}$$
![[Pasted image 20230515121456.png]]

### Low Pass Filter
The following low pass filter has the following transfer function
$$\mathbf{H}(\omega)=-\cfrac{R_2}{R_1}\cfrac{\omega_c}{j\omega+\omega_c}$$
where $\omega_c=\cfrac{1}{R_2C}$
![[Pasted image 20230515121914.png|centre|300]]
#### Low Pass Filer Example
Find the cutoff frequency:
![[Pasted image 20230515122944.png|300]]
$$Z_2=\cfrac{1}{\cfrac{1}{R_2}+j\omega C}=\cfrac{R_2}{1+j\omega CR_2}$$
$$\therefore v_{out}=-\cfrac{R_2}{\cfrac{1+j\omega CR_2}{R_1}}$$
$$=-\cfrac{R_2}{R_1}\cfrac{\cfrac{1}{R_2C}}{j\omega+\cfrac{1}{R_2}{C}}$$
The cutoff frequecny is: $\omega_c=\cfrac{1}{R_1C}=100rad^{-1}$
Gain is: $-\cfrac{R_2}{R_1}=-10$

### High Pass Filter
The following high pass filter has the following transfer function
$$\mathbf{H}(\omega)=-\cfrac{R_2}{R_1}\cfrac{j\omega}{j\omega+\omega_c}$$
where $\omega_c=\cfrac{1}{R_2C}$
![[Pasted image 20230515122031.png|centre|300]]
#### High Pass Filter Example
Find the cutoff frequency:
![[Pasted image 20230515122142.png|300]]
$$v_{out}=-\cfrac{R_2}{R_1+\cfrac{1}{j\omega C}}$$
$$=-\cfrac{j\omega R_2}{j\omega R_1+\cfrac{1}{C}}$$
$$=-\cfrac{R_2}{R_1}\cfrac{j\omega}{j\omega+\cfrac{1}{R_1C}}$$
The cutoff frequency is equal to: $\omega_c=\cfrac{1}{R_1C}=1000 rad^{-1}$
Gain is: $-\cfrac{R_2}{R_1}=-10$


