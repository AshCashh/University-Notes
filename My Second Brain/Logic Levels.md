#cs
In digital circuits, a logic level is one of a finite number of states that a digital signal can inhabit. For digital input/output (IO), conventionally:
- The [[Voltage]] level of the positive power supply represents a logical 1, or the high state
- 0 V (ground) represents a logical 0, or the low state.

The QUTy is supplied 3.3V so that when a [[Digital Outputs]] is high, the voltage present on the corresponding pin will be around 3.3V. Because voltage is a continuous quantity, we must discretise the full range of voltages into logical levels using **thresholds**.
- A voltage **above** the input **high** threshold $t_H$ is considered **high**
- A voltage **below** the input **low** threshold $t_L$ is considered **low**.
The interpretation of a voltage between these states is determined by [[Hysteresis]].