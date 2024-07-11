---
tags: [cs]
Created: 2023-06-27T14:15:42+10:00
Modified: 2024-07-03T19:35:33+10:00
---
A push-pull digital output is the most common form of output used in [[Digital Outputs]]. It is commonly formed using two [[Transistors]] which act like [[Switches]]. The output driver A *drives* the output state *Y* to:
- HIGH by connecting the output net to the supply voltage +V
- LOW by connecting the output net to the ground voltage GND (0V)
![[Pasted image 20230316203721.png|center|300]]
Hence the output state *Y* is determined by the logic level of the output driver *A*. $Y=A$

The push-pull output *Y* can both source and sink [[Current]] from the connected net.

