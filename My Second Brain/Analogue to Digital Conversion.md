---
alias: ADC
---
#cs
## Analogue to Digital Conversion
Analogue signals or [[Sinusoidal Signals]] to digital signals conversion (ADC) is a technique used to convert an analogue signal to a digital signal. The analogue signal is sampled at a regular interval and the sampled value is converted to a digital value. Digital quantities are both discrete in amplitude and time. 

Specialised hardware called an analogue to digital converter performs this function. An ADC takes a sample of a continuous signal at an instant in time, if the signal is time-varying it takes multiple samples. The quality of the conversion depends on a number of factors, such as resolution and sample rate.

Often performed in two steps:
1. Sampling - relates to Sampling Theory
2. Quantisation
![[Pasted image 20230824113251.png]]
### Sampling
When we discretise in time, this is referred to as sampling. The sampling rate determines the time resolution and introduces aliasing error. On a [[Microprocessors & Microcontrollers|Microcontroller]], time resolution is typically the period of the CPU clock.
![[Pasted image 20230501212643.png]]

# Sampling Theory
Given a signal $x(t)$ with a maximum frequency $f_m$, the sampling theorem states that the signal can be perfectly reconstructed from a sequence of samples if the sampling frequency $f_s$ is at least twice the maximum frequency:
$$f_s \geq 2f_m$$
where $f_s$ has units of samples per second. 

When the sampling frequency is exactly twice the maximum frequency, the signal is sampled at the Nyquist rate (or frequency). The Nyquist rate ensures that the signal does not alias, i.e., the copies of the signal in the frequency domain do not overlap.

### Example
Consider the analogue signal given by:
$$x(t)=15cos(100\pi t)$$
a) Determine the minimum samples rate to avoid aliasing:
$$f_m=1/T=1/2\pi/100\pi=50Hz $$
$$f_s=2f_m = 2*50=100\space \text{samples per second}$$
b) Determine the sampled signal values, $x(n)$ if the sampling rate is 200Hz ($f_2$):

Evaluate $x(t)$ for $t=n/f_s$:
$$x(n)=15cos\left(2\pi\times\frac{nf}{f_s} \right)=15cos(100/200)\pi n$$
$$x(n)=15cos(\pi n/2)$$

c) Determine the sampled signal values, if the sampling rate is reduced to 75Hz:
$$x(n)=15cos\left(2\pi\times\frac{nf}{f_s} \right)=15cos(100/75)\pi n$$
$$x(n)=15cos(4\pi n/3)$$


# Anti-Aliasing 
When the maximum frequency of the signal is greater than half the sampling frequency, the signal will alias. To prevent aliasing, an anti-aliasing (low-pass) filter is used to eliminate spectral overlap before sampling. While this process removes high frequency information, it ensure that the signal is reconstructed correctly.

When Aliasing occurs, different frequencies will overlap and hence be added together and amplify. This will result in muffled sounds
# Quantisation
When we discretise in amplitude, this is referred to as quantisation. Each amplitude is assigned a digital code. The code width determines the amplitude resolution and introduces quantisation error.
![[Pasted image 20230501212606.png]]

Digital signals are discrete in both time and amplitude. A quantiser transforms each sampled value to take on of $L$ distinct levels. The $L$ levels are allocated over the entire dynamic range of the analogue signal:
$$x_{min} \leq x(t)\leq x_{max}$$
This procedure is non-invertible.

## Uniform Quantisers 
A uniform quantiser divides the dynamic range ($x_{max}-x_{min}$) into $L$ equal intervals, known as quantisation levels. The step size $\Updelta$ between quantisation levels is calculated by: (measured in V)
$$\Updelta = \cfrac{x_{max}-x_{min}}{L}$$
Many applications have $x_{max}=-x_{min}$, so the step size is:
$$\Updelta = \cfrac{2x_{max}}{L}$$
The number of levels $L$ is usually a power of two:
$$L=2^n
$$
where $n$ is the number of bits to encode $L$ levels.

### Example
A signal with a dynamic range between $\pm 4$ V is to be uniformly quantised with each level encoded by 4 bits. What is the step size between quantisation levels?
$$
\begin{align}
&n=4\space\text{bits} \\
&L=2^4=16\space\text{Levels} \\
\\
\Updelta&=\frac{2x_{max}}{L}=\frac{2*4}{16}=0.5V
\end{align}
$$
4 bits allows the encoding of 16 unique code words. Each code word corresponds to a single quantisation level:
$$
\begin{align}
&0000&0001&\qquad0010&0011 \\
&0100&0101&\qquad0110&0111 \\
&1000&1001&\qquad1010&1011 \\
&1100&1101&\qquad1110&1111 \\
\end{align}
$$



## Uniform Quantisers Types
From the example, the following types exist.
**Mid-Tread Type**:
- Enforces a quantisation step at $0$V
- L is odd if $x_{max}=-x_{max}$
- May waste one level
![[Pasted image 20230824132450.png|300]]

**Mid-Riser Type**:
- $L$ levels evenly distributed on either side of $0$V
- Can't guarantee $0$V DC
- Uses all levels when $x_{max}=-x_{max}$
![[Pasted image 20230824132523.png|300]]

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