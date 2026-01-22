# Enhancing the CPU

Even after 50 years, the principle of operation for an Intel or AMD CPU should be recognisable from the simple descriptions in these notes up to now. To finish this technology introduction, I want to talk about some of the enhancements that have been used to speed up and generally improve the performance of processors.

And then the law of unintended consequences kicks in. In recent years, some of the most intractable vulnerabilities in PC hardware were introduced by these enhancements.

## Floating Point Calculations
As we have described a CPU, it is a general purpose machine for calculating numbers and manipulating numbers which could represent things like characters. You should have covered _ASCII_ and _Unicode_ in one of my other modules, if you don’t remember, do an internet search on those terms now. However the registers in a CPU are of a fixed size; in modern processors either 32 or 64 bits wide. That means the smallest and biggest numbers we can describe are limited by the size of the register. 

- What is the biggest _integer_ you can describe in a 32 bit register?  
- What is the biggest _signed integer_ you can describe in a 32 bit register?

If you don’t remember, do an internet search on those terms now.

You should understand _scientific notation_, if you are rusty, revise independently. If I want to express the number one thousand in scientific notation, I can write it as 1 x 10^3^. If I want to write 1/1000 in scientific notation I can write it as 1 x 10^-3^. Before we go on, make sure you remember all this! If you don’t remember, do an internet search on those terms now. The principle of scientific notation is that we split a number into a _fraction_ and an _exponent_.

<figure>
<img src = "https://jor-donegal.github.io/CPU101/images/table6.jpg">
<figcaption>Table 6. Floating point examples .</figcaption>
</figure>

We can describe very big and very small numbers in the computer in exactly the same way. Imagine we have a 32 bit register to describe numbers; we call this _single precision floating point_. We could store the fraction part of the number in the first 24 bits and the exponent in the last 8. The exponent must be signed so only 7 digits could be used to represent numbers and our exponent could range from -127 to +128 (why?). _Double precision floating point_ uses 64 bits where 53 digits are used for the fraction and 11 bits are used for the exponent. Giving one bit for the sign, that gives us an exponent range of -1022 to + 1023. We can now describe very large and very small numbers.

The floating point examples given here refer to the IEEE version of floating point. There are variations out there and you may find floating point data which does not match the description above!

## Co-processors
But a CPU is a general purpose computing device, it was never designed to cope with these very large numbers. It was designed for _signed integer values_, not floating point. Early PCs did their floating point calculations in a slow and cumbersome way. The chip manufacturers developed special chips specifically to do floating point; these were called co-processors. So for example, the 8086 processor could have an 8087 _co-processor_ installed beside it to enhance its number crunching capabilities.

By the 1990s, the chip manufacturers had begun to integrate the co-processor onto the same silicon die as the processor. From the 80486DX onwards, the processor in most personal computers has included the co-processor. If you check the block diagram of any modern CPU, your will find a floating-point unit.

## Cache
Once microprocessor clock speeds went faster than 16Mhz (around 1990!) we ran into a performance mismatch; CPUs became faster than main memory. The architecture of main memory is called _Dynamic Random Access Memory_ or DRAM and it has the characteristics of being cheap with a low component count per bit. Each bit is stored as charge on a capacitor, with as little as two transistors controlling the charge. The downside is that DRAM is relatively slow. We could use _Static RAM_ or SRAM, This looks like the memory we built with D Flip Flops, but it has a very high component count per bit and is thus very expensive, takes a great deal of space on the silicon, uses a lot of power, etc.
There was no easy fix for this, there is still no good solution today. 

The way we get around the problem is to have a very large, slow, cheap main memory using DRAM. We then have a much smaller fast expensive _cache memory_ using SRAM. Most programmes run sequentially, one instruction following the other. When we have to read an instruction from memory, we could just as easily read a full kilobyte of instructions from main memory to cache. When we need the next instruction from memory, instead of making a slow call to main memory, we can make a call to the much faster cache memory. This is an _instruction cache_.
Similarly, if we are going to operate on a piece of data, there is a really good chance that the next piece of data we are going to need is right beside the one we just used. We call this _spatial locality_. If we have previously used a piece of data, there is a high chance we will use it again. This is called _temporal locality_. The fact that we can prove both of these things to be statistically predictable gives us the ability to size and design our cache and the algorithms to decide how to operate it. This is a _data cache_. 

When we look for an instruction in cache and it is there, great! We call that a _cache hit_ and it means that we are operating at maximum efficiency. If not, we have a big delay seeking the data from main memory. This process might be 1,000 times slower than getting the information from the cache. We call this a _cache miss_.

We will look at cache memory, DRAM and SRAM in more detail later in the course.

## Pipelining
In our simple CPU models, an instruction ripples through the registers of the CPU, taking quite a few clock cycles to complete. Why not break up the activities required by an instruction into a number of steps and do each of these steps concurrently? Consider the steps an ordinary instruction might make (Fig 7). 

<figure>
<img src = "https://jor-donegal.github.io/CPU101/images/table7.jpg">
<figcaption>Table 7. Flow of a single instruction .</figcaption>
</figure>

Now suppose we run one instruction after another through the stages. As one as an instruction had finished a stage, the next instruction can use the subsystems required by that stage!

<figure>
<img src = "https://jor-donegal.github.io/CPU101/images/table8.jpg">
<figcaption>Table 8. Pipeline flow of a single instruction .</figcaption>
</figure>

At clock cycle 1
- Execute instruction 1. The first part of the cycle is the instruction fetch. 

At clock cycle 2
- Instruction 1 can move to the decoder
- Execute instruction 1. The first part of the cycle is the instruction fetch. 

At clock cycle 3 
- Instruction 1 can move to reading operands from memory
- Instruction 2 can move to the decoder
- Execute instruction 3. The first part of the cycle is the instruction fetch. 

By the fifth clock cycle, 5 instructions are being simultaneously executed through hardware designed only for single processing. As you can imagine, this can massively enhance performance. A modern Intel processor may have up to 20 stages in its _pipeline_.

## Logical Processors
Taking this idea a little further, we can get a CPU to act like it is two logical CPUs. Two separate _threads of execution_ can be multiplexed into the same CPU. Intel calls this technology hyperthreading. If you look at task manager on your laptop and check the performance tab, you'll see sockets, cores and logical processors.

- Socket: the physical silicon on the motherboard, a single chip on most laptops, multiple on servers.
- Core: inside that single chip, we can have multiple CPUs or _cores_ which can share resources on the chip, like cache memory.
- Logical Processors: using a technology like hyperthreading, give each physical core two threads of execution.

To be clear, two threads of execution into a single core does not give the same performance as two cores. Often it's quoted as a 40% increase in performance. Particularly in the world of virtualization hosts, we need to be cognizant of this. There are times when a hypervisor might be optimised by switching off hyperthreading.





