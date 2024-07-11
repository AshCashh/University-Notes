---
tags: [ee]
Created: 2024-02-26T12:34:40+10:00
Modified: 2024-07-03T19:35:33+10:00
---
In [[Electronics]], a Schmitt trigger is a comparator [[Circuit]] that makes use of positive feedback (small changes in the input lead to large changes in the output) to implement [[Hysteresis]] and is used in [[Analogue to Digital Conversion]]

## How Does a Schmitt Trigger Work?
A Schmitt trigger makes use of positive feedback - it takes a sample of the output and feeds it back into the input so as to 'reinforce', so to speak the output - which is the exact opposite to negative feedback which tries to nullify any changes to the output.

This reinforcing property is useful, it makes the comparator decide the state of the output it wants and makes it stay there.
![[Pasted image 20240226230854.png|centre|400]]
## Schmitt Trigger Oscillator
Having two thresholds gives Schmitt triggers the 555 like ability to act like predicable oscillators.
![[Pasted image 20240226231159.png|centre|300]]

Assume that the capacitor is initially uncharged. The gate detects this as an input low and sets the output high, since its an inverting gate. The capacitor begins charging through the resistor. Once the upper threshold is reached the gate flips to output low, discharging the capacitor to the low threshold, providing a predicable frequency output.

This expression for frequency can be derived with the following:
$$f= \cfrac{1}{T}\approx\cfrac{1}{K\times RC}$$
The K-factor for a 74HC14 can be found on its datasheet.
![[Pasted image 20240226231634.png|centre|300]]
