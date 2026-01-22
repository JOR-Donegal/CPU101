# Digital Logic and Memory

The first computer systems (e.g. ENIAC) required programmes to be hard wired, literally with jumper cables, dials and switches. A computer at the time looked like something out of a bad sci-fi movie!  

From 1944 and the development of the EDIVAC computer, work began on holding computer programmes and data in electronics memory. In 1945 Jon Von Neumann proposed that a working computer system should consist of a processing unit or ALU, a control unit, and memory. We have looked at the ALU and at control in previous notes, let’s take a look at memory!

Firstly some terminology. 
A _bit_ is a single binary digit and can be a one or a zero
A _nibble_ is a group of 4 bits
A _byte_ is a group of 8 bits
A _word_ is a group of 16 or more bits, we can have 32 bit words, 64 bit words etc.

In previous notes, we have built the bones of a simple 4 bit computer. Can we provide this computer with a small amount of 4-bit memory?

We know that we could store bits in a register, so building a memory element for a single 4 bit nibble will be quite easy. In fact, the design is that of a _4 bit register_. As previously, we will _clock_ the circuit. When write is enabled, whatever is on the input bus will be copied to the registers. They can then be read at the output bus an unlimited number of times. Once write enabled is switched off, any changes in the input bus will not be copied to the memory element. So now we have a single memory element, good to store a single nibble of data, fig 21. 

<figure>
<img src = "https://jor-donegal.github.io/CPC101/images/fig21.png">
<figcaption>fig 21. 4 bit register.</figcaption>
</figure>

How do we scale that up to make a useful quantity of memory?

When we design memory, we tend to do so as a grid of rows and columns. Imagine a spreadsheet where we lay out the memory. We have a 4 bit computer, each column could be one 4 bit nibble and we can populate the grid with ones and zeros.

<figure>
<img src = "https://jor-donegal.github.io/CPU101/images/table4.jpg">
<figcaption>Table 4. Data in 4x3 memory.</figcaption>
</figure>

We can only read/write one nibble at a time, so we are going to need to be able to select which nibble we want to read from. Let’s call that the address of the nibble of data. So we need some way to select the correct address.

<figure>
<img src = "https://jor-donegal.github.io/CPU101/images/table5.jpg">
<figcaption>Table 5. Addressing in 4x3 memory.</figcaption>
</figure>