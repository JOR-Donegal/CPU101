# Modern CPU Design
In previous notes we have seen how basic memory elements work (latches and flip-flops). On their own, this would not be very useful. But we can combine several memory elements together to create a register, a very fast but very small memory store. We have also seen how we can use simple circuits to add two numbers together and we have built and manipulated an Arithmetic Logic Unit or ALU. We have taken a look at main memory and at this stage you should understand how memory stores data in fixed sizes (nibble, bytes or words) in unique addresses. With these elements, we have the basic ingredients, but we are missing the key elements to tie it all together to make a workable computer system. Let’s do that now!

Firstly, we need to get an idea of how a CPU functions. It’s actually very simple and it’s called the fetch-execute cycle; or sometimes the fetch-decode-execute cycle (Fig 26). A CPU runs like clockwork (literally, everything runs off an electronic pulse called a clock). A computer programme is a list of instructions which the CPU will run through in sequence. 

<figure>
<img src = "https://jor-donegal.github.io/CPU101/images/fig26.png">
<figcaption>Fig 26. fetch-decode-execute cycle .</figcaption>
</figure>

Let’s imagine we have a programme with 20 steps, starting at step zero. 
We need to keep track of where we are in the sequence and to do that we have a special register called the programme counter or PC, initially set at zero (or to the location of the start of the programme). As programmes run sequentially, the PC will normally have an increment function.

To fetch an instruction from memory, we transfer the contents of the programme counter to another special register, the _Memory Address Register_ or MAR. The MAR can assert an address on to the address bus, which will control where main memory points to. The contents of that memory location will then be available on the data bus. These contents can then be read by a special register, the _Memory Buffer Register_ or MBR.  The contents of the MBR then get transferred to another special register, the _Current Instruction Register_ of CIR. The instruction in the CIR is one of the instructions in the CPUs instruction set. It might be a command like __ADD__, __SUBTRACT__, __LOAD__, etc. We execute this command and then increment the programme counter and run through another cycle. The CPU just keeps doing this……forever!

<figure>
<img src = "https://jor-donegal.github.io/CPU101/images/fig27.png">
<figcaption>Fig 27. fetch-decode-execute in blocks .</figcaption>
</figure>

There is a simple algebra we can use to describe what is going on. We use names to refer to registers and memory and we use names [in square brackets] to refer to the contents of the register or memory. We use arrows to indicate the flow of data. S

- MAR ← [PC]
- PC ← [PC] + 1
- MBR ← [Memory]
- CIR ← MBR

Next we need to look at how the instruction in the CIR gets executed. 

The CPU needs to be able to “understand” what the instruction means. In reality, there is some _decoder logic_ which looks at the bits in the instruction and activates blocks of digital logic based on what the instruction was. In previous notes, we saw an adder or subtractor. Suppose we said that bit zero of the instruction in the CIR would get hooked up to the subtract button of the ALU. In this case, any instruction with bit 0 = 0 would activate the add functionality. Any instruction with bit zero = 1 would activate the subtract functionality. We can encode a different instruction for every combination of binary digits in the CIR. An eight bit CIR would give us the ability to encode 2^8^ or 256 different instructions.

An instruction to __ADD__ or __SUB__ (subtract) on its own would have no utility; add what? For most instructions we have to pass the values that we want the instruction to work on, for example, the two numbers we want to add together. The data an instruction will execute against are called __operands__. For example, the ADD instruction 0x00 might be an instruction which means “take the two next values in memory after this instruction and add them together”. Or for a multiply instruction, take the value in a general purpose register and _successively add_ the contents of the accumulator that many times.

The next question…where do we put the results of a calculation?

Many processors support the idea of a special register called the _accumulator_. This is the key register where we perform calculations or place our results.  

<figure>
<img src = "https://jor-donegal.github.io/CPU101/images/fig28.png">
<figcaption>Fig 28. ALU support .</figcaption>
</figure>

Alternatively, some processors have many general purpose registers. An ADD instruction might be specifically designed to take the contents of two specified general purpose registers and put the result in the accumulator. Your smartphone and the ubiquitous Raspberry Pi both use ARM processors, these have 16/32 registers which can be used for almost any purpose. 

We have already looked at simple models of the ALU and there isn’t that much more to add. We know that the ALU has control inputs to determine what functions it will run (e.g. ADD, SUB, MULT, DIV). We also know that it needs inputs to provide it with operands (Fig 29).
It also has to have a way of getting the results out. In our examples, we show all these separately. In real processors, there is great variation in how this is done. 

<figure>
<img src = "https://jor-donegal.github.io/CPU101/images/fig29.png">
<figcaption>Fig 29. ALU signals .</figcaption>
</figure>

In reality, although we might have three internal busses connecting to the ALU, there is only going to be one data bus in the computer, which everything shares. At some point, the data for Bus A and B will have to come into the processor and the data from Bus C will have to be written back to memory. Our control logic orchestrates all this via a device called a _multiplexor_. On the diagram (Fig 30), why do we show only two select lines?

<figure>
<img src = "https://jor-donegal.github.io/CPU101/images/fig30.png">
<figcaption>Fig 30. A 4:1 mux .</figcaption>
</figure>

The final components we need to have before we can have a working data bus is the buffer or _tri-state_. Only one device can put information on a data or address bus, if more than one device asserts the bus, there will be chaos! We have a component called a tri-state which is like an electronic switch. When you need to connect a device to the data bus, you enable the tri-states which connects each line in the bus to the device. When you no longer want to connect to the bus, you disable the tri-state. 

<figure>
<img src = "https://jor-donegal.github.io/CPU101/images/fig31.png">
<figcaption>Fig 31. Tristate .</figcaption>
</figure>

So now let’s bring together everything we have learned, to sketch a fully working CPU, with external connectivity.

<figure>
<img src = "https://jor-donegal.github.io/CPU101/images/fig32.png">
<figcaption>Fig 32. Summary .</figcaption>
</figure>

With a real CPU and computer
- We have a range of busses interconnecting the internal components within the CPU. 
- The internal data bus within the CPU would allow a vale to be transferred to/from the accumulator to/from almost any register. 
- The MBR is bi-directional, we can either read data off the data bus or write data to the data bus, based on the address asserted in the MAR.
- The external data, address and control bus are shared amongst all the components of the computer.
- Everything is orchestrated by the control unit, both inside the CPU and via the external control bus.
- There will be buffering between each internal component and the internal data bus. Only one internal component will be able to write to the internal data bus at a time. This is determined by the control unit.
- 	Multiplexor/De-multiplexor blocks will be used to enable multiple devices to share the same busses
- 	There will also be buffering between memory chips and the data bus. Complex encoder/decoder logic allows the correct memory chips to be selected and the correct rows/columns activated.

That’s it for simple CPU design. We now having a working central processor. Keep in mind though, I have made this as simple as possible, with the minimum components to describe a workable system. We have only scratched the surface. A real CPU has a great deal more complexity and has many more add-ons to increase performance. However, if you can follow what we have covered to date, the add-ons will all make sense! 







