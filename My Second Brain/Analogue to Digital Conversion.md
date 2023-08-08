#cs
## Analogue to Digital Conversion
Analogue signals or [[Sinusoidal Signals]] to digital signals conversion (ADC) is a technique used to convert an analogue signal to a digital signal. The analogue signal is sampled at a regular interval and the sampled value is converted to a digital value. Digital quantities are both discrete in amplitude and time. 

Specialised hardware called an analogue to digital converter performs this function. An ADC takes a sample of a continuous signal at an instant in time, if the signal is time-varying it takes multiple samples. The quality of the conversion depends on a number of factors, such as resolution and sample rate.

### Sampling
When we discretise in time, this is referred to as sampling. The sampling rate determines the time resolution and introduces aliasing error. On a [[Microprocessors & Microcontrollers|Microcontroller]], time resolution is typically the period of the CPU clock.
![[Pasted image 20230501212643.png]]

### Quantisation
When we discretise in amplitude, this is referred to as quantisation. Each amplitude is assigned a digital code. The code width determines the amplitude resolution and introduces quantisation error.
![[Pasted image 20230501212606.png]]

## Configuring the ATtiny1626 ADC
To use the ATtiny1626 ADC function, the following things need to be configured:
- The ADC clock and timebase (affects conversion time, accuracy)
- The reference used by the ADC
- Sample duration (how long the input signal is sampled each conversion)
- How sampling is triggered (by event or free-running)
- Which input is to be sampled (input multiplexing)
- ADC mode (including resolution)

## Analogue input on the ATtiny1626
There is only a single analogue source; the potentiometer R1, which is connected to PA2 (AIN2)
![[Pasted image 20230501213954.png|200]]

## ADC Potentiometer Example
```c
void adc_init(){
	// Enable ADC
	ADC0.CTRLA = ADC_ENABLE_bm;
	// /2 clock prescaler
	ADC0.CTRLB = ADC_PRESC_DIV2_gc;
	// Need 4 CLK_PER cycles @ 3.3MHz for 1us, select VDD as ref
	ADC0.CTRLC = (4 << ADC_TIMEBASE_gp) | ADC_REFSEL_VDD_gc;
	// Sample duration of 64
	ADC0.CTRLE = 64;
	// Free running, left adjust result
	ADC0.CTRLF = ADC_FREERUN_bm | ADC_LEFTADJ_bm;
	// Select AIN2 (potentiometer R1)
	ADC0.MUXPOS = ADC_MUXPOS_AIN2_gc;
	// Select 12-bit resolution, single-ended
	ADC0.COMMAND = ADC_MODE_SINGLE_12BIT_gc | ADC_START_IMMEDIATE_gc;
}
int main(void){
	uint16_t result;

	adc_init();
	serial_init();

	while(1) {
		// 12-bit result in bits 15..4
		result = ADC0.RESULT;
		// print the most significant 8 bits
		printf("%02X\n", result >> 8);

		// wait 1 second
		_delay_ms(1000);
	}
}
```
## ADC Events and Interrupts
As ADC conversions take time, we will often want to set up hardware to take care of the sampling process for us, this will free up the CPU to perform other computations. To start a conversion we can set up the ADC to use events e.g. setup a timer to trigger the ADC to start a conversion at regular intervals

Similarly, we can set up interrupts that are triggered when a conversion is complete and a result is ready to be read from the ADC result register.