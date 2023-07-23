#ee
An amplifier is a device for increasing the [[Power]] of a signal through an external energy source. In an electronic amplifier, the "signal" is usually a [[Voltage]] or [[Current]]
![[Pasted image 20230423193952.png]]

The gain *K* of an amplifier, is the ratio of the output signal to the input signal:
$$ v_{out} = Kv_{in}$$
An operational amplifier (op amp) amplifiers the voltage difference between its input terminals. Operational amplifiers require a power supply to amplifer voltage. In an operational amplifier:
- The output cannot exceed the power supply range
- The inputs should remain within the power supply range
![[Pasted image 20230423194515.png]]

Inside an op amp:
![[Pasted image 20230423194546.png]]
$v_p$ is greater than $v_n$ so turn $v_o$ up 
$v_p$ is less than $v_n$ so turn $v_o$ down
$v_p$ is equal to $v_n$ so leave $v_o$ as it is

## Golden Rules of Op Amps
1. The inputs draw no currents: $i_p=i_n=0$
2. The voltage difference between the inputs is driven to zero by the output: $v_p=v_n$

## Op Amp Analysis
![[Pasted image 20230423204332.png]]
##### Inverting Amplifier
![[Pasted image 20230423200154.png]]
Suppose circuit is in steady state with input and output at 0V.
What will $v_n$ be when you apply 1V at the input?

Using a [[Voltage#Voltage Divider|voltage divider]]:
$$v_n = v_{in}\cfrac{R_2}{R+R_2}$$
$$=1\cfrac{10000}{1000+10000} = 0.91V$$
Voltage at non-inverting input is less than inverting input so output voltage will fall.
What is $v_n$ when the output voltage stops falling?

The output voltage is stable when the voltage $v_n$ and $v_p$ are equal. 
Using the voltage divider circuit, what must the voltage at the output be?

Finding current: $1=v/r=1/1000 =1mA$
Ohms law: $v=iR=1mA \times 10k= 10V$
Because of current the circuit will reach steady state when the output is $-10V$

Therefore this amplifier has a gain of -10

Use KCL at inverting input to create an equation that balances currents through the resistors, remembering no current goes into op-amp input
![[Pasted image 20230423201822.png]]

KCL at $v_n$: $i_1 + i_2 =0$
$$ i_1 = \cfrac{v_{in}-v_n}{R} $$
$$i_2 = \cfrac{v_{out}-v_n}{R_2}$$
Sub into KCL equation:
$$\cfrac{v_{in}-v_n}{R_1} + \cfrac{v_{out}-v_n}{R_2} = 0$$
Voltage at output is stable when: $v_n=v_p=0$
Therefore:
$$\cfrac{v_{in}}{R_1}+\cfrac{v_{out}}{R_2}=0$$
Rearrange for $v_{out}$
$$v_{out}=-\cfrac{v_{in}R_2}{R_1}$$
This is an inverting amplifier
The gain of the amplifier is $-R_2/R_1$

##### Voltage Follower / Voltage Buffer
Use the golden rules to work out what this circuit does
![[Pasted image 20230423202812.png]]
$$v_n = v_p$$
$$v_{out} = v_n$$
$$v_{out} = v_{in}$$
Think about a mechanical amplifier, the amplifier adds torque but doesnt affect velocity. In this sense, the amplifier doesnt affect voltage, it affects current.
##### Non-Inverting Amplifier

This is an amplifier circuit where $v_{out} = Kv_{in}$. We can use the golden rules to find K.
![[Pasted image 20230423203354.png]]
Use Rule 1 to find an expression for voltage $v_n$ with respect to $v_{out}$

Expression for $v_n$ using voltage divider:
$$ v_n=v_{out}\cfrac{R_1}{R_1+R_2}$$
Now use Rule 2 to find $v_n$ with respect to $v_{in}$

Rearrange previous expression for $v_{out}$:
$$v_{out}R_1=v_n(R_1+R_2)$$
$$v_{out}=\cfrac{(R_1+R_2)}{R_1}v_n=\left(1+\cfrac{R_2}{R_1}\right)v_n$$
Equate the two expressions to find K for amplifier equation:
$$ K = \cfrac{R_1+R_2}{R_1}=1+\cfrac{R_2}{R_1}$$



## Op Amp Analysis 2
![[Pasted image 20230423212810.png]]
##### Summing Amplifier
Find the relationship between $v_a,v_b,v_c,v_{out}$ 
![[Pasted image 20230423211804.png]]
Remember: $v_p=v_n=0$ and $v_p=v_n$
Using KCL: $i_1+i_2+i_3+i_4 = 0$
Combining with voltage divider:
$$ \cfrac{v_a-v_n}{1000} + \cfrac{v_b-v_n}{1000}+\cfrac{v_c-v_n}{1000}+\cfrac{v_{out}-v_n}{1000}=0$$
Since $v_p=v_n=0$
The relationship simplifies to:
$$v_a+v_b+v_c+v_{out}=0$$
Therefore,
$$v_{out}=-(v_a+v_b+v_c)$$

##### Difference Amplifier
Find the relationship between $v_a,v_b,v_{out}$
![[Pasted image 20230423212722.png]]
Remember: $v_p=v_n=0$ and $v_p=v_n$

Using KCL: $i_1+i_2=0$
Combining with voltage divider:
$$\cfrac{v_a-v_n}{1000}+\cfrac{v_{out}-v_n}{10000}=0$$
Using voltage divider:
$$v_p=v_b\cfrac{10000}{1000+10000}$$
I aint writing all that lol
![[Pasted image 20230423212656.png]]


## Op Amp Design Problem
Design an op-amp circuit to compute the following function:
$$ v_{out} = -(2v_a+5v_b)$$
Step 1: Select the most suitable op-amp circuit configuration: Inverting summing amplifier

Step 2: Draw the circuit and analyse it to obtain the general equation OR use formula of inverting summing amplifier if known
![[Pasted image 20230423213324.png]]

Step 3: Compare the general equation with the desired function, $v_{out} = -(2v_a+5v_b)$ and select resistor values

General formula: $v_{out}=-\left(\cfrac{R_2}{R_a}v_a+\cfrac{R_2}{R_b}v_b\right)$
Want: $\cfrac{R_2}{R_a}=2$, $\cfrac{R_2}{R_b}=5$
Choose $R_2=10k\ohm$
Sub in: $R_a=\cfrac{10000}{2}=5k\ohm$, $R_b=\cfrac{10000}{5}=2k\ohm$
Note: Do not choose very small values for resistors. At least between $1k\ohm < 100k\ohm$
![[Pasted image 20230423214440.png]]

## Practical Op Amps
Real operational amplifiers have limits to their capabilities:
1. Finite voltage gain
2. Limited output voltage range 
3. Limited output current (25mA)
4. Slew Rate (0.5V/$\micro$s)
5. Offset voltage (2mV)
6. Finite input resistance (2M$\ohm$)

## Finite Gain and Saturation Model
![[Pasted image 20230423220358.png]]
![[Pasted image 20230423220413.png]]

### Saturation Problem
What voltage is required to at the input to force the output into saturation, if the open loop voltage gain is 200V/mV?
![[Pasted image 20230423215830.png|200]]

$v_0=A(v_p-v_n)$
$v_p-v_n=\cfrac{V^+}{A}$
$v_{in}=\cfrac{10}{200v/mV}=1/20mV$

