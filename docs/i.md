# Alternative Processor Paradigms
So far on this module we have looked at the technologies used in workstations, servers and laptops. 
For the past forty years, this market has been controlled by Intel and a few additional players like AMD. 

_Reduced Instruction Set Computers_ (RISC) is a processor design using simple hardware and highly optimized instruction sets.
They are faster per instructions, physically smaller and simpler and as a result, more power efficient. 
## RISC
When we look into the actual execution of instructions in a processor, we can identify empirically (by experimentation and real data) which instructions are used most, which take most processor time. A processor is a number cruncher, so you would guess that arithmetic logic instructions would be executed most? 

Wrong! 

A processor spends more time shifting data in and out of memory than doing anything else. The second most common thing for it to do is to control the flow of program execution. Optimization techniques such as _pipelining_ and _caching_ are intended to optimize this.  

Reduced Instruction Set or RISC processors were first defined in a 1980 paper by Patterson and Ditzel [1] and early experimentation with RISC in Berkeley exposed some of the characteristics of this model.
 
- Processors were kept as simple as possible with fixed instruction sets or fixed length. 
- Instructions which process data only operate on registers, not on memory, speeding up and simplifying processing.
- There are many registers, typically thirty two. This was far in excess of the handful of registers in a typical CISC processor.
- Instruction decoding is hard wired. CISC processors were so complex, they required microcode in the core to assist decoding.
- There is a concentration of optimization strategies like pipelines.

The emergent properties of this strategy were that die sizes were much smaller, with fewer transistors in a smaller silicon chip. This resulted in less power consumption, a shorter development time, and for a range of complex reasons, better performance and reduced costs.
 
### Advanced RISC Machines (ARM) processors
Acorn Computer Ltd. (Cambridge, England) developed the first commercial RISC chip in the mid-1980s, the ARM processor [2]. They have an interesting business model. They develop the instruction sets, tools and specifications and then license the production of chips to large silicon foundries. 

ARM is now the most widely used instruction set worldwide. Early chips shipped were 32 bit; but from 2011, a 64 bit version (ARMv8) has been available. The ARM contains all the components for a computer on a single silicon die; it is therefore a _System on a Chip_ or SoC. The instruction set design is what we would expect from RISC. Instructions are simple and most instructions execute in a single clock-cycle. If you want to work with an ARM based system, a Raspberry PI is a cheap and easy solution. You can load a full copy of Linux (the standard is a derivative of Debian Linux). 

The cost of a board like the Raspberry Pi 5 is about €50, depending on memory etc.

## Microcontrollers
A vast amount of devices need simple, low power (in terms of both compute and consumption) controllers. Since the late 1970s controllers such as the _Peripheral Interface Controller_ (PIC) have been used for embedded systems and small systems control.  A modern PIC will be programmable with on board flash memory. Typically a PIC will be programmed in Basic, C or C++ and will have simple and widely available tools, code examples and application notes. 

In machine code, there are a very limited number of instructions (40-80) and they are all fixed in length. There is one accumulator register (W0) which holds the results of all the calculations. Oddly, the RAM used for data is also used for storing temporary values etc. This memory is used like it was a series of registers which map into RAM. Memory is mostly 8 bit although this varies with higher end PICs.

Programs are stored in a separate memory location, normally in flash RAM, so they are non-volatile. 

There is a stack, but it is implemented in the hardware, separately.

[1] Patterson, D.A. and Ditzel, D.R., 1980. The case for the reduced instruction set computer. ACM SIGARCH Computer Architecture News, 8(6), pp.25-33.

[2] Furber, S.B., 2000. ARM system-on-chip architecture. Pearson Education.

## Graphics Processor Units (GPU)
Original video cards began as devices without onboard calculation capability, beyond simple memory operations. 
The arcade game industry pushed the limit of these techniques. The first dedicated display processors began to emerge in the 1980s. 
From the 1990s, cards were developed to take load off the CPU and perform graphics operations indendently.
_Graphics Processor Units_ were deleloped as video cards for complex rendering, typically for game technology. 

I'm not going to dig in to them further here. If you are interested in AI/ML then do some independent reading now. In particular, read about nVIDIA technology and CUDA.


