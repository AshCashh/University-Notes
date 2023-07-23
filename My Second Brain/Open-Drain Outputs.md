#cs
Multiple [[Push-Pull Outputs]] should never be connected to the same net as when one output is driven HIGH and another is driven LOW, and effective [[Short Circuit]] is created and one or more devices may be damaged. While push-pull outputs with an output enable may be used, the timing must be carefully managed.

Hence a more robust solution is to use open-drain outputs
An open-drain output is either:
- In the [[High-Impedance Outputs|high-impedance state]], where the [[Pull-up & Pull-down Resistors|pull-up resistor]] is used to pull the net to the high state when the net is not driven low.
- Connected to ground, when the net is driven low.