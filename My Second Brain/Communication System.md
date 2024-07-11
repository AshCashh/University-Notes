---
aliases:
  - telecommunication system
tags:
  - ee
Created: 2024-07-11 18:38
Modified: 2024-07-11T18:38:53+10:00
---
A communications system can be summarised by the following block diagram:
![[Pasted image 20240702125553.png|center]]
where
- $m(t)$ is the information message signal (prior to conditioning for transmission)
- $s(t)$ is the conditioned signal for transmission
- $n(t)$ contains channel noise and interference
- $r(t)$ is the received signal 
- $\hat{m}(t)$ is the reconstructed received message signal (where $\hat{m}(t)$ usually approximates $m(t)$) 
## Transmitter
The transmitter carries out **signal conditioning** by transforming the signal to a more appropriate form before transmission through the channel. Some examples of signal conditioning are shown below:
- [[Electronic Filters]] like Low-Pass Filtering which restricts signal bandwidth to avoid wasting signal power on frequencies that are not transmitted by the channel and to avoid interference with other signals.
- [[Analogue to Digital Conversion]] (ADC) produces a digital word which represents a sample of the analog message waveform.
- Carrier [[Modulation]] transfers the signal to a frequency band that is suitable for transmission through the channel.
## Channel
A communication channel refers to the physical medium that carries the signal from the transmitter to the receiver. There are two types of channels:
1. [[Cables|Wired]]: Twisted pair copper telephone lines, waveguides, coaxial cables, fibre-optic cables.
2. [[Wireless]]: Air, vacuums, sea water, optical fibres
General principles of communications always apply regardless of the type of channel. However, certain conditioning methods are better suited to certain channels. 

Chanels often attenuate signals (reduce their amplitude or strength) through:
- Random noise
- Interference from other sources
and therefore, it is a key consideration in the design of a communications system.
## Receiver 
The receiver acts as the inverse of a transmitter. The receiver: 
1. **Demodulates** the received signal by stripping the carrier from the received signal $r(t)$. 
2. **Filters** out noise and interference from the demodulated signal.
3. **Reconstructs** an estimate of the original message signal $\hat{m}(t)$.
Due to the finite nature of the SNR, the estimated output of an analog signal can never be exactly equal to the original signal (A perfect reconstruction would require an infinite SNR which is unrealistic). However, it is often possible to reconstruct a digital signal exactly using error detection and correction techniques at the receiver. 

## Information Sources
An information source can be classified as either **analog** or **digital**. Analog signals can be modulated or transmitted directly or converted to digital data and transmitted using digital modulation techniques.

An analogue signal to be transmitted is called the message signal and is denoted $m(t)$. The spectral components of this signal lie within a finite bandwidth $W$, such that $M(f)=0$ for $|f|>W$, where $M(f)$ is the Fourier Transform of $m(t)$. This signal's bandwidth is limited to prevent interference with other signals. 

Many kinds of message signals can be considered:
- Audio
- Video
- Computer Data
- Telemetry (measurements)
- Soundings (RADAR, SONAR) 
- A mixture of the above (i.e., data over voice)
