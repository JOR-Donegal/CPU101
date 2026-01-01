# Automation and I/O
As PICs are commonly used for automation, we have a whole new set of terms to describe how to interface with the outside world. We have to be careful here. A PIC will require signals with particular characteristics, such as high and low voltage. The process you are working with (whatever you are automating or controlling) may use completely different signal levels. You may need to come up with conditioning circuitry to interface the two. 

For example. I like to use Raspberry Pi as a basic controller and _Internet of Things_ (IoT) device. It has a general purpose input/output interfae (GPIO) for digital singals. But it expects +/- 3.3VDC and almost any higher voltage will do physical damage to the board. I cannot connect an RS232 interface without chaning volatge levels. I may need a _relay_ board to switch voltage/power. Look up electromechanical relays, in this context they are logic controlled switches.  


### Digital Input (DI)	
A binary signal, a high voltage is one and a low voltage is zero. High and low voltage are defined by the circuit, typically 5VDC and 0VDC.

### Digital Output (DO)	
A binary signal, a high voltage is one and a low voltage is zero. High and low voltage are defined by the circuit, typically 5VDC and 0VDC. The current output is very limited, so if you are switching lights or a motor, you will need relays or additional switching electronics.

### Analogue Input (AI)	
An analogue to digital converter (ADC) take real world variable voltages and converts them into digital signals. The two important points are, how frequently does the ADC sample (for example, a sound card may sample at 44kHz) and how many bits per sample (8 bits per sample would allow for 256 discrete levels).

### Analogue Output (AO)	
A _digital to analogue converter_ (DAC) takes a digital numeric value and converts it into an analogue voltage level. As with analogue inputs, it will do so at a frequency and in certain steps, depending on the resolution of the DAC.

### Pulse Input (PI)	
Many processes emit pulses. For example, one way of measuring speed and distance is to have a magnet at one point on a wheel. As it passes a sensor, the sensor emits a pulse. Counting these pulses in a fixed time (e.g. one second) allows the frequency of revolution of the wheel to be estimated.

### Pulse Output (PO)
Some processes may be controlled by a pulsed output, where either the number of duration of pulses controls an actuator. Stepper motors (used in robotics) are an example of a device which could be controlled by pulses. 





