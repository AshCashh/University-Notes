---
tags: [ee]
Created: 2023-06-27T14:15:42+10:00
Modified: 2024-07-03T19:35:33+10:00
---
Hysteresis refers to the property of a system whose state is dependent on its history. In [[Circuit|Electric Circuits]], this avoids ambiguity in determining the state of an input as it switches between [[Voltage]] levels.
![[Pasted image 20240226221412.png|centre|400]]
Given a transition: 
- If an input is currently in the low state, it has not transitioned to the high state until the voltage crosses the high input voltage threshold.
- If an input is currently in the hight state, it has not transitioned to the low state until the voltage crosses the low input voltage threshold.
It is therefore always preferable to drive a digital input to an unambiguous voltage level.