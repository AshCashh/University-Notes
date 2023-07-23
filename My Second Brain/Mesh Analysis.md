#ee
### Definitions
**Node:** A point where two or more [[Circuit Elements]] join
**Essential Node:** A point where three or more circuit elements join
**Loop:** A path with the same start and end node
**Mesh:** A loop that does not enclose any other loops

## Mesh Analysis Steps
1. Label the unknown mesh currents
2. Find voltage across each of the circuit elements in terms of mesh currents
3. Use [[Kirchhoff's Laws#Voltage Law (KVL)|KVL]] around each mesh to create simultaneous equations
4. Solve simultaneous equations for mesh currents
5. (optional) Find the node voltages. Check power balance

### Example:
1. Label the unknown mesh currents in a clockwise direction:
![[Pasted image 20230318190204.png|300]]
2. Find the current in each resistor:
![[Pasted image 20230318190419.png|300]]
Find the voltage across each of the elements:
![[Pasted image 20230318190704.png|300]]
3. Use KVL around each mesh
![[Pasted image 20230318191522.png|300]]
4. Solve the simultaneous equations:
![[Pasted image 20230318210127.png|300]]
5. Identify the nodes and calculate the voltage 
![[Pasted image 20230318210601.png|300]]
Check the power balance:
![[Pasted image 20230318211011.png|300]]

## Mesh Analysis on dependent sources
Mesh analysis also works with dependent sources

1. Label the unknown mesh currents
![[Pasted image 20230319130128.png|300]]
2. Find voltage over circuit elements
![[Pasted image 20230319130209.png|300]]
3. Use KVL to create equations:
$$0=6-i_1-2(i_1-i_2)$$
$$ 0=2(i_1-i_2)-3i_2-4i_x$$
Simplify and sub that $i_x=i_1-i_2$
$$6=3i_1-2i_2$$
$$0=-2i_1-i_2$$
Solve for $i_1$ and $i_2$
$$i_1 = 6/7A,\space i_2=-12/7A,\space i_x=18/7A$$
4. Identify the node voltages
![[Pasted image 20230319131314.png|300]]
