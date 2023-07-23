#ee
Root mean square (rms) is a method of obtaining a useful average of a signal that is symmetric about the horizontal axis. It is defined as the square root of the mean value of the function squared. For a sine wave:
$$ V_{rms} = \cfrac{V_m}{\sqrt{2}},\phantom{AAA} I_{rms} = \cfrac{I_m}{\sqrt{2}}$$
where $V_m/I_m$ is the magnitude

#### RMS Example
![[Pasted image 20230430162442.png|300]]
Find the RMS value:
$V_m=340V$ 
$V_{RMS}=\cfrac{340}{\sqrt{2}}=240V$

What is the frequency in Hz?
Find the period (t=0 -> t=20ms): 20ms
Frequency: $f=\cfrac{1}{0.02}=50Hz$


## RMS Voltage, Current and Power
In a resistive load, the [[Power]] can be determined using the RMS [[Current]] and RMS [[Voltage]]:
#### RMS Voltage:
$$v=\sqrt{2}V_{rms}cos(\omega t+ \phi)$$
#### RMS Current:
$$i=\sqrt{2}I_{rms}cos(\omega t+ \phi)$$
#### RMS Power:
$$V_{rms}I_{rms}(1+cos(2\omega t+ 2\phi))$$
Average power:
$$P_{avg} = V_{rms}I_{rms}$$
#### Voltage, Current, Power in a Resistor Example
Find the power dissipated in a 240V, 100W light bulb:
$$p=100W$$
Find the current flowing in a 240, 100W light bulb:
$$I=\cfrac{P}{V}=\cfrac{100}{240}=0.42A$$
