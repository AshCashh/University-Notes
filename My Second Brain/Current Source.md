#ee
A current source is a [[Circuit Elements|Circuit Element]] that produces or dissipates [[Power]] with a specified [[Current]] at whatever voltage is required.
- Indicated by the arrow encapsulated in a circle. 
- The arrow indicates the direction of the current. 
![Pasted image 20230222181706.png](app://local/Users/ashasaunders/Downloads/ash's%20vault/PNGs/Pasted%20image%2020230222181706.png?1677053826238)

## Characteristics 
![[Pasted image 20230311142120.png|200]]
- Supplies constant current regardless of the voltage

## Current Sources in Parallel Circuits
According to [[Kirchhoff's Laws]]. The sum of all currents into a node equals zero, this law is applicable when multiple current sources are within a [[Parallel Circuits|Parallel Circuit]]
Kirchoff Current Law (KCL) gives:
$$ i_1 + i_2 + i_3 = i $$
The equivalent current source would put the same current through the resistor, so:
$$ i_{eq} = i_1 + i_2 + i_3 $$
Therefore, **current sources in parallel are summed.**

## Mesh Analysis
Easy case: Current source in a single mesh.
Treat mesh as known current and solve:
![[Pasted image 20230319100322.png|400]]

Trickier: Current source between meshes.
Create supermesh: a special mesh that surrounds the current source
![[Pasted image 20230319101928.png|400]]
Write supermesh equation:
$$ i_2 - i_1 = 8\space or\space i_1 - i_2 = -8 $$
Use KVL around super mesh:
$$ 0 = 6-2i_1-3i_2-2i_2 $$
$$ 6 = 2i_1 + 5i_2 $$
Solve:
$$ i_2 = 22/7, \space i_1 = -34/7 $$
