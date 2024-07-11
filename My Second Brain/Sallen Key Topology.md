---
tags: [ee]
Created: 2024-04-22T11:54:30+10:00
Modified: 2024-07-03T19:35:33+10:00
---
The Sallen-Key topology is an [[Electronic Filters|Electronic Filter]] used to implement [[Second Order Systems|Second Order System]] active filters that is particularly valued for its simplicity. 

# Sallen Key Circuit
The general circuit form for a second order voltage controlled voltage source (VCVS) consists of:
![[Pasted image 20240422121245.png]]
After nodal analysis the following expressions can be derived:
$$\begin{align}
v_a&=\cfrac{1}{Y_1+Y_2+Y_4}(v_{in}Y_1+v_pY_2+v_0Y_4)\\
v_p&=\cfrac{Y_2}{Y_2+Y_3}v_a\\
v_n&=\cfrac{Y_6}{Y_5+Y_6}v_0\\
\end{align}
$$
After a big of algebra the following transfer function is derived:
$$\cfrac{v_0}{v_{in}}=\cfrac{Y_1Y_2(Y_5+Y_6)/Y_6}{(Y_2+Y_3)(Y_1+Y_2+Y_4)-Y_2^2-Y_2Y_4(Y_5+Y_6)/Y_6}$$
After substituting RC values:
![[Pasted image 20240422122013.png]]

$$\cfrac{v_0}{v_{in}}=\cfrac{\cfrac{K}{R_1R_2C_1C_2}}{s^2}$$