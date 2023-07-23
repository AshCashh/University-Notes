#ee #cs
When no devices are actively driving a net (e.g. all connected outputs are in the [[High-Impedance Outputs|HiZ]] state), the state of the net is not well defined. Hence we can use a **pull-up** or **pull-down** [[Resistor]] to ensure that the state of the pin is always well-defined

- When no circuitry is actively driving the net, the resistor will passively pull the [[Voltage]] to either the voltage supply, or ground
- When another device actively drives the net, the active device defines the voltage of the net. Hence the [[Current]] from the resistor is simply sourced or sunk by the active device.
The resistors used as pull-up and pull-down resistors are typically in the k$\ohm$ range.

