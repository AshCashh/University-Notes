#cs #ee
An integrated circuit (IC) is a set of electronic [[Circuit|Circuits]] (typically) implemented on a single piece of semiconductor material, usually silicon. ICs comprise of hundreds to many thousands of [[Transistors]], [[Resistor|Resistors]] and [[Capacitor|Capacitors]]; all implemented on silicon. ICs are packaged and connections to the internal circuitry are exposed via pins.

In general, the specific implementation of the IC is not important, but rather the function of the device and it interfaces with the rest of the circuit. Hence ICs can be treated as a functional black box. For digital ICs
- Input pins are typically [[Impedance#High Impedance|High Impedance]], and they appear as an [[Open Circuit]]. 
- Output pins are typically low-impedance and [[Push-Pull Outputs]], and will actively drive the voltage on a pin and any connected circuity to a high or low state. They can also drive connected loads.

## Interfacing to Integrated Circuits
This generally means that we can interface an IC by connecting its pin directly to the pins of a microcontroller
- For IC inputs, the microcontroller pin is configured as an output, and the microcontroller sets the logic level of the net.
- For IC outputs, the microcontroller pin is configured as an input, and the IC sets the logic level of the net
As microcontroller pins are typically configured as inputs on reset, a [[Pull-up & Pull-down Resistors|Pull-up & Pull-down resistor]] may be required if it is important for an IC input to have a known state prior to the configuration of the relevant microcontroller pins as outputs.