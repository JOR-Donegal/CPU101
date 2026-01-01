# Components
Modern devices abstract way thier internal complexity. I want to try to explain how a computer works from the component level upwards. 
These notes are extracted from undergraduate Computer Architecture material I wrote c. 2014. 

The fundamental components we use in every electrical circuit include:
## Resistors
Resistors are two-terminal devices that restrict, or resist, the flow of current. The larger the resistor the less current can flow through it for a given voltage as demonstrated by Ohm’s law: V= I*R. 

Electrons flowing through a resistor collide with material in the resistor body, and it is these collisions that cause electrical resistance. These collisions cause energy to be dissipated in the form of heat or light (as in a toaster or an old incandescent light bulb). 

Resistance is measured in Ohms (Ω) and an ohm is defined by the amount of resistance that causes 1A of current to flow from a 1V source. 

The amount of power (in Watts) dissipated in a resistor can be calculated using the equation P= I*V = I^2^R A resistor that can dissipate about 5 Watts of power would be about the size of a pen and a resistor that can only dissipate 1/8 Watt is about the size of a grain of rice. 

If a resistor is placed in a circuit where it must dissipate more that its intended power, it will melt!

A standard colour coding scheme exists for resistors and any experienced electronics person can tell the value of a resistor at a glance! However, as the number of colur bands can vary, it’s always better to check with a _digital volt meter_ (DVM).

Look up resistor colour coding now.

## Capacitors
A capacitor (called a condenser in the old days!) is a passive two-terminal device that can store electric energy in the form of charged particles. A capacitor is like a reservoir of charge that takes time to fill and empty. 

The construction of capacitors is more varied than that or resistors, but the general principle is that two conductive plates are separated by is non-conductive dielectric.

When there is a potential difference (voltage) across the conductors, a static electric field develops across the dielectric, causing positive charge to collect on one plate and negative charge on the other plate. 

Energy is stored in the electrostatic field.

The voltage across a capacitor is proportional to the amount of charge it is storing, the more charge added to a capacitor of a given size, the larger the voltage across the capacitor. It is not possible to instantaneously move charge to or from a capacitor, so it is not possible to instantaneously change the voltage across a capacitor. It is this property that makes capacitors useful in many applications.

Capacitance is measured in Farads. A one Farad capacitor can store one Coulomb of charge at one volt. For engineering on a small scale (i.e., hand-held or desk-top devices), a one Farad capacitor stores far too much charge to be of general use (it would be like a car having a 1000 gallon petrol tank). 

More useful capacitors are measured in micro-farads (uF) or pico-farads (pF). The terms "milli-farad“ and "nano-farad" are rarely used. Large capacitors often have their value printed plainly on them, such as "10 uF" (for 10 microfards).

## Inductors
An inductor (also called a choke or coil) is a passive two-terminal electrical device that stores energy. Although this sounds a bit like a capacitor, it is different in that a capacitor stores energy in an electric field, an inductor stores it in its magnetic field. 
In practical terms, inductance is the characteristic of an electrical circuit that opposes the starting, stopping, or a change in value of current. Even a perfectly straight length of wire has some inductance. Current flowing in a conductor produces a magnetic field surrounding the conductor; when the current changes, the magnetic field changes. This causes a relative motion between the magnetic field and the conductor, and a back electromotive force (EMF) is induced in the conductor. The polarity of the back electromotive force is in the opposite direction to the applied voltage of the conductor. The overall effect will be to oppose a change in current magnitude.
Some effects we may notice are that the start-up current drawn by an electric motor is much higher than the current required to run the motor (the coil has to “charge”).   

The symbol for inductance is L and the basic unit of inductance is the HENRY (H). To quantify the unit, an inductor with an inductance of 1H produces an EMF of 1V when the current through the inductor changes at the rate of 1A per second.

In appearance, an inductor can be as simple as a coil of copper wire. They can be cylindrical-shaped or torus shaped (the engineer’s term for shaped like a doughnut!)

More commonly, an inductor will have a core of a ferromagnetic material.  The core material has the effect of increasing the magnitude of the magnetic field and reducing its physical size.

## Diodes
Very frequently we need electronic components which can act like one way valves; current will only pass one way through the device, it will not pass back.
These devices are called diodes. They are two terminal devices and are used for a range of purposes. They consist of two layers of a semiconductor (normally silicon) sandwiched together. 

Almost every power supply will have a few diodes combined with a transformer and a few capacitors.

One version of the diode is the LED or light emitting diode. A property of the joint between the two layers causes light to be emitted. 

## Transistors
A transistor is an active electronic device with (at least) three terminals. They generally consist of three layers of a semiconductor (normally silicon) sandwiched together. 

A transistor can act like an amplifier. A voltage or current applied to an input control terminal to change the current flowing through another pair of output terminals; this property is called gain. Because the controlled power can be higher than the controlling power, a transistor can amplify a signal. This is the basis for the audio subsystems of all amplifiers, stereo systems, iPods, etc.

A transistor can act also like a switch. When no voltage is applied to an input control terminal, no current flows through another pair of output terminals. Alternatively, when a voltage over a particular threshold is applied to the input control terminal, then current flows through the output terminals.  This is the basis for digital logic and all modern binary computers.

Because the controlled power can be higher than the controlling power, a transistor can switch a large current using only a small controlling current. This is the basis of all power electronics.

The original transistors we used were called bipolar transistors. 

These are three terminal active devices that can conduct current between two terminals (the collector and the emitter) when a third terminal (the base) is driven by an appropriate signal.

The transistor switches used in modern digital circuits are called “Metal Oxide Semiconductor Field Effect Transistors”, or MOSFETs or just FETs. FETs are also three terminal devices that can conduct current between two terminals (the source and the drain) when a third terminal (the gate) is driven by an appropriate logic signal.
FETs can be thought as electrically controllable ON/OFF switches



