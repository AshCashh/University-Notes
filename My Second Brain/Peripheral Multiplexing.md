#cs
Pins can be used to connect internal peripheral functions to [[Hardware Peripherals]]. As [[Microprocessors & Microcontrollers|microcontrollers]] have more peripheral functions than avaliable pins, peripheral functions are typically multiplexed onto pins.

Multiplexing is a method by which multiple peripheral functions are mapped to the same pin. In this scenario, only one function can be enabled at a time, and the pin cannot be used for GPIO.
- Peripheral functions can be mapped to different sets of pins to provide flexibility and to avoid clashes when multiple peripherals are used in an application. 
- When enabled, peripheral functions override standard port functions. 
- The Port Multiplexer (PORTMUX) is used to select which pin set should be used by a peripheral. 
- Certain peripherals can have their input/outs mapped to different sets of pins through the PORTMUX.
- 