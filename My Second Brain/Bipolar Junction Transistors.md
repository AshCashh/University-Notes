---
aliases:
  - BJT
tags:
  - ee
Created: 2024-03-10T13:07:32+10:00
Modified: 2024-07-03T19:35:33+10:00
---

![[Pasted image 20240310131143.png|centre|400]]
A bipolar function [[Transistors|Transistor]] (BJT) is a three-terminal device in which a small current applied to the base controls a much larger current flowing between the collector and emitter. It is available in two flavours (NPN and PNP), with properties that meet the following rules for NPN transistors (for PNP simply reverse all polarities):
1. **Polarity**: The collector must be more positive than the emitter
2. **Junctions**: The base-emitter and base-collector circuits behave like [[Diodes]]
![[Pasted image 20240310131305.png|centre|300]]
3. **Maximum Ratings**: Any given transistor has maximum values of $I_C, I_B,$ and $V_{CE}$ that cannot be exceeded with out costing the exceeder the price of a new transistor.
4. **Current Amplifier**: When rules 1-3 are obeyed, $I_C$ is roughly proportional to $I_B$ and can be written as: 
   $$I_C=h_{FE}I_B=\beta I_B$$
   - Where $\beta$ is the current gain (sometimes called $h_{FE}$) and typically about 100. Both $I_B$ and $I_C$ flow to the emitter

Rule 4 gives the transistor its usefulness: a small current flowing into the base controls a much larger current flowing into the collector.

## Transistor Switch
![[Pasted image 20240313195417.png|centre|300]]
This application in which a small control current enables a much larger current to flow in another circuit is called a transistor switch. When the mechanical **switch is open**, there is no base current. So, from rule 4, there is no collector current (the lamp is off). When the **switch is closed**, the base rises to 0.6V (base-emitter diode is in forward conduction). The drop across the base resistor is 9.4V so the base current is 9.4mA. Blind application of Rule 4 gives $I_C=940\text{mA}$. This is wrong. Why? Because Rule 4 holds only if Rule 1 is obeyed: at a collector current of 100mA the lamp has 10V across it. To get a higher current you would have to pull the collector below ground (a transistor cant do this). Hence it results in whats called *saturation* - the collector goes as close to ground as it can (typical saturation voltages are about 0.05-0.2V) and stays there. In this case, the lamp goes on with its rated 10V across it.

There are certain cautions to be observed when designing transistor switches:
1. Choose the base resistor conservatively to get plenty of excess base current, especially when driving lamps, because of the reduced beta at low $V_{CE}$. This is also a good idea for high-speed switching, because of capacitive effect and reduced beta at very high frequencies.
2. If the load swings below ground for some reason (e.g., it is driven from AC or it is inductive), use a diode in series with the collector (or a diode in the reverse direction to ground) to prevent collector-base conduction on negative swings
3. For inductive loads, protect the transistor with a diode across the load, as shown in Fig 2.6. Without the diode the inductor will swing the collector to a large positive voltage when the switch is open, most likely exceeding the collector-emitter breakdown voltage.
![[Pasted image 20240313201311.png|centre|300]]
You may ask why we are bothering with a transistor, and all its complexity, when we could just use that mechanical switch alone to control the lamp or other load. There are several good reasons: 
1. A transistor switch can be driven electronically from some other circuit, for example a computer output bit
2. Transistor switches enable you to switch very rapidly, typically in a small fraction of a microsecond
3. You can switch many different circuits with a single control signal
4. Mechanical switches suffer from wear and their contacts "bounce" when the switch is activated, often making and breaking the circuit a few dozen times in the first few milliseconds
5. With transistor switches you can take advantage of remote cold switching, in which only DC control voltages snake around through cables to reach front-panel switches