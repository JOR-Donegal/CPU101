# Memory
In this section, I am going to build up gates into useful subsystems, first memory!

## The Set/Rest Latch
The first thing that we needed to do useful calculations with these gates was to have a way of storing numbers (remember, all numbers are represented in binary within the computer); this is the concept of _memory_. We need a circuit which can store a single bit of data; we call a circuit like this a _latch_. There are several types of latch available in TTL which were built into early computers (and are now integrated into much larger circuits).

<figure>
<img src = "https://jor-donegal.github.io/CPU101/images/fig8.jpg">
<figcaption>Fig 8. SR Latch.</figcaption>
</figure>

One of these simple circuits was the _set-reset latch_ or _S-R Latch_. Very simple, if you raise the input S to a one, Q will set to 1 and ¯Q will reset to 0. If you raise the R input to 1, Q will reset to 0 and ¯Q will set to 1. Work your way through the circuit to confirm this!

One of the problem with this circuit is that if you raise S and R to 1 at the same time, the circuit acts in an unpredictable manner. Again, try working your way through the circuit to see.

Up to now, all the digital gates and circuits we have looked at have been deterministic, that means that for the inputs given, there is only one possible outcome. Once we start dealing with circuits which can store bits (memory) we need to understand the concept of _state_; a circuit can be in a particular state before we encounter it and the output of any action may depend on the state the circuit was in before we started.

## Clocks and Timing
In a real computer, most things are synchronised by a timing signal. Have a look at the circuit below where we introduce a timing signal, known as a _clock_. The AND gates block any inputs from either S or R until the clock signal is high. Now we can control when the set or reset command are sampled.

<figure>
<img src = "https://jor-donegal.github.io/CPU101/images/fig9.jpg">
<figcaption>Fig 9. Clocked SR Latch.</figcaption>
</figure>

## The D Latch
In a D Latch, we allow only one input, directly to the set AND gate at the top of the diagram, and via an inverter to the reset AND at the bottom of the diagram. When D=1 and the clock signal is high, we set Q=1. When D=0 and the clock signal is high, we reset Q=0. Work your way through the circuit to confirm this. This is a pretty good circuit but there is one issue. The clock pulse is quite wide and the latch can be set at any stage while the pulse is high. This is none too precise, especially when we are trying to get the maximum speed and performance out of our electronics. 

<figure>
<img src = "https://jor-donegal.github.io/CPU101/images/fig10.jpg">
<figcaption>Fig 10. D Latch.</figcaption>
</figure>

## Edge Detection
One of the ways we can get best performance out a clocked circuit is to activate the circuit or the edge of the pulse rather than on the pulse itself. Consider the circuit below. Each gate has a propagation delay to activate. Suppose each gate takes 1 ns to activate and a starts as 0. If a is at 0 then b must be at 1 because of the inverter. When the pulse goes high at a it goes high at c at the same time. However, the inverter causes a delay of 1 ns before b becomes 0. For this brief period, both b and c were 1 and the AND gate output becomes 1 for this brief time period. We have detected the rising edge of the pulse.

<figure>
<img src = "https://jor-donegal.github.io/CPU101/images/fig11.jpg">
<figcaption>Fig 11. Edge Detection.</figcaption>
</figure>

One other interesting thing we can do here is to detect both the rising and falling edge. That would give us a good narrow pulse at double the rate of the clock. I wonder where we might come across Double Data Rate (DDR) being used. Try an Internet search if you haven’t come across this before.

We can use an edge trigger circuit to trigger a D Latch to make it much more precise. In the circuit below, the clock is intercepted by a trigger circuit to make an edge-trigger circuit. A latch which is edge triggered is called a flip-flop.

<figure>
<img src = "https://jor-donegal.github.io/CPU101/images/fig12.jpg">
<figcaption>Fig 12. Flip-flop.</figcaption>
</figure>

Flip-flops are very commonly used in all kinds of digital logic circuits. There are several different block circuits used. To keep things simple, we abstract the details away. We can treat a half adder like a black box, not worrying too much about what is inside it. This allows us to simplify our diagrams, getting more and more unnecessary detail out of the way so we can understand more complex circuits more easily.

- A D Latch is triggered by a positive clock
- A D Latch is triggered by a negative clock
- The triangle indicates a positive edge triggered flip-flop
- The triangle and circle indicates a negative edge triggered flip-flop

<figure>
<img src = "https://jor-donegal.github.io/CPU101/images/fig13.jpg">
<figcaption>Fig 13. Triggering.</figcaption>
</figure>

By combining four flip-flops in an array, we can create a four bit memory store, a store which could hold half a byte of information. We could use this as memory, or we could use it as a temporary area to store data that we need to process; we call this a _register_.

<figure>
<img src = "https://jor-donegal.github.io/CPU101/images/fig14.jpg">
<figcaption>Fig 14. 4 bit memory.</figcaption>
</figure>

When the circuit starts up, everything is at zero. I set values for D0 to D3 on the input bus. When the values are set and I want to write to the register, I toggle the write switch. This enables the clock through the AND gate and creates an edge to clock the D flip flops. They then store whatever is on the input bus. The output is available on the output bus indefinetely or until it is overwritten or the power is removed. 

As with all things computing, once we understand how something complex works inside, we build an abstraction to hide the detail. A block diagram of a register might look something like this.

<figure>
<img src = "https://jor-donegal.github.io/CPU101/images/fig15.jpg">
<figcaption>Fig 15. 8 bit register.</figcaption>
</figure>

Some registers have a very defined purpose and will have extra functionality built into their logic. For example, there are times when we need sequential counters, these may have functions like increment or decrement built in.  
Some mathematical manipulations require us to shift the bits in a register left or right, this may also be built in. 



