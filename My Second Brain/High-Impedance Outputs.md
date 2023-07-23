#cs
In many instances, a [[Digital Outputs|Digital Output]] is required to be placed in a [[Impedance#High Impedance|High-Impedance]] (HiZ) state. This is accomplished by using an output enable (OE) signal.

- When the OE signal is HIGH, the output state Y is determined by the output driver $A$.
- When the OE signal is LOW, the output state Y is in a high-impedance state.

When the output is in high-impedance (HiZ) state:
- The output is an effective [[Open Circuit]], meaning it has no effect on the rest of the circuit
- The voltage on the ouput net is determined by the other circuitry connected to the net
HiZ outputs are typically used when multiple devices need to signal over the same wire(s) (half-duplex communications bus).