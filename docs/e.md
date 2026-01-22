# Processor Architecture

The key component in any computer is the Central Processor Unit or CPU. This does all the calculating and co-ordination for the entire computer.

In previous notes we have seen how basic memory elements work (latches and flip-flops). On their own, this would not be very useful. But we can combine several memory elements together to create a _register_, a very fast but very small memory store. If we wanted to do a calculation, we could put numbers in two registers and if we knew how to do so, we could add them together and put the result in a third register. 

We have also seen how we can use simple circuits to add two numbers together. In Boolean logic, that if you can add, you can multiply using _successive addition_. We can also use some Boolean maths to make essentially the same circuit do subtraction. If we can do subtraction, we can also do division by _successive subtraction_ . So our simple adder can be quite a powerful calculating circuit. In a CPU the circuitry to do these calculations is referred to as an _Arithmetic Logic Unit_ (ALU).

Before we could make a useful calculating machine, we need some way to tie all of these things together. The pathways which allow parts of a computer to communicate with other parts of the computer are called a bus. It would be nice if we knew when things worked or didn’t work, if we had some status flags to indicate when a calculation fails or returns a number that is too big. The final thing we are going to need is some _control logic_ to hang all these things together and to synchronise everything we want to happen. So here is my design for a simple CPU, (fig19)!

<figure>
<img src = "https://jor-donegal.github.io/CPU101/images/fig19.png">
<figcaption>fig 19. An ALU block diagram.</figcaption>
</figure>

You already know how to build one of these! We know how to make a register and we know how to make an adder/subtractor. So all we really need to do is to hang it all together. Below there is a diagram of a 4 bit adding/subtracting machine. You may think this is not very impressive, but remember, the world’s first micro-processor was an Intel 4004, a 4 bit processor built for early calculators.

<figure>
<img src = "https://jor-donegal.github.io/CPU101/images/fig20.png">
<figcaption>fig 20. An ALU block diagram.</figcaption>
</figure>

There are a few differences between our simple CPU and a real, usable CPU/computer. Most computers will require more functionality than add and subtract. For us to do repetitive addition, we would need to build additional circuitry. We could load the number to be multiplied into register A and the number it is to be multiplied by in register B. Then we would need the digital logic to add A to A, B number of times. Not a lot of circuitry, but more than we can cover in a brief course. For every instruction which we add in hardware, we make the CPU bigger, more expensive, more complex, and more power-hungry. There has been a debate for decades now as to which is the correct approach. Processors which have few instructions but are fast and cheap are called _Reduced Instruction Set Computers_ or RISC. Expensive processors which are billions of transistors and hundreds of instructions are call _Complex Instruction Set Computers_ or CISC. All modern PCs use CISC processors. All modern smartphones use RISC. Tablets are a mix, Apple/Android all use RISC, some Windows tablets use CISC.

In a real computer, we need somewhere to keep our instructions (or programmes) and our data. This is main memory and we will look at that next.  


