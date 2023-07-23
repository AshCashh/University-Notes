#ee
A Light-Emitting [[Diodes|Diode]] (LED) is a semiconductor device that emits light when [[Current]] flows through it. 

## Driving LEDs
The brightness of an LED is proportional to the current passing through it. As LEDs are non-ohmic, we cannot drive them directly with a [[Voltage]] as this would result in an uncontrolled flow of current that may damage the LED or driver.
Instead, LEDs are paired with a [[Resistor#Resistors in Series|series resistor]] to limit the flow of current. The appropriate current is dependent on the specific LED that is used and the capability of the driver device (microcontroller). A typical indictor LED requires a current of 1mA to 2mA.


## Interfacing to LEDs
An LED can be driven in two different configurations from a microcontroller pin:
- Active high; in which case the LED is lit when the pin is HIGH
- Active low; in which case the LED is lit when the pin is LOW
Both of these configurations have their benefits and the best configuration depends entirely on the context.

On the QUTy, the LED display is driven in the active low configuration. This has a number of advantages
- If the internal [[Pull-up & Pull-down Resistors|pull-up resistors]] are mistakenly enabled, no current will flow into the LEDs
- The [[Microprocessors & Microcontrollers|microcontroller]] pins can sink higher currents than they can source, allowing us to drive the display to a higher brightness
- The display used on the QUTy has a common anode configuration, hence we must use an active low configuration to drive the display segments independently 
An LED is an example of a simple digital output, as we can map logical states to LED states (lit or unlit) for a [[Digital Outputs|digital output]].