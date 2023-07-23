#ee
A switch is a [[Circuit Elements|Circuit Element]] used to connect and disconnect different elements in a circuit

A switch can be open or closed:
- In the open state, the switch will not conduct current
- In the closed state, the switch will conduct current

Switches can take a variety of forms:
- Poles - the number fo circuits the switch can control
- Throw - the number of output connections each pole can connect its input to
- Momentary or toggle action
- Different form factors, e.g. push button, slide, toggle, etc

Switches are typically used for user input:
![[Pasted image 20230312151212.png|400]]

## Switches as digital inputs
The state of a switch can be used to set the state of a pin. As the switch has two states (open or closed), these can be mapped directly to logical states (0 or 1). This can be done by connecting the switch between the pin and voltage source representing one of the logic levels (ground or a positive supply)
![Pasted image 20230314001611.png](app://local/Users/ashasaunders/Downloads/ash's%20vault/Pasted%20image%2020230314001611.png?1678716971100)
- When the switch is open, the [[Pull-up & Pull-down Resistors]] is used to define the state of the switch.
	- Alternative: (When the switch is open, the pin will be disconnected from this voltage source, so we also need a pull-up/pull-down resistor to set the state of the pin when the swithc is open)
- When the switch is closed, the state of the pin is defined by the voltage connected to via the switch
	- Alternative: (When the switch is closed, the voltage on the pin will be the same as the voltage source it is connected to via the swithc)

## Interfacing to switches
As with LEDs, we can interface switches to microcontroller pins in two different configurations:
- Active high, in which case the pin will be high when the switch is closed
- Active low, in which case the pin will be low when the pin output is closed
![200](app://local/Users/ashasaunders/Downloads/ash's%20vault/Pasted%20image%2020230314002034.png?1678717234475)
An active low configuration is usually preferred as:
- It allows for the utilisation of an internal [[Pull-up & Pull-down Resistors|pull-up resistor]] that is commonly implemented in microcontrollers
- It eliminates the risk of unsafe [[Voltage]]s being applied to the pin from the power supply in an active high configuration
- It is easier to access a ground reference on a circuit board.