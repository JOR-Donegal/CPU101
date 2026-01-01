# Calculation

We now know how to do basic digital logic and how to create basic memory elements. The next thing we need to be able to do is to manipulate numbers stored in those memory elements.

When we add two binary numbers together, what are the possible outcomes?

<figure>
<img src = "https://jor-donegal.github.io/Background26/images/table1.jpg">
<figcaption>Table 1. Simple addition.</figcaption>
</figure>

So to add two binary numbers, we will need outputs for a sum and a carry. Let’s do a truth table and figure out how this should work.

<figure>
<img src = "https://jor-donegal.github.io/Background26/images/table2.jpg">
<figcaption>Table 2. Simple addition, truth table.</figcaption>
</figure>

Make sure this makes sense to you before reading on! Can you figure out what gate matches the sum column…what gate give a 1 output when either input is one, but a 0 output when both gates are 1? 
You should know this! 
Look at the carry column. What gate give a 1 output only when both inputs are 1? 
If you couldn’t figure this out, go back and read the notes on logic gates again.

A circuit to perform this simple mathematical function is called a _half-adder_ (for reasons we will see later!). I have built a half-adder circuit to test it. I have used two memory elements (D flip flops) to store my A and B values. I have included the XOR and AND gates and have put in some lights so I can see what is going on. I tested it and it works!

<figure>
<img src = "https://jor-donegal.github.io/Background26/images/fig16.jpg">
<figcaption>fig 16. A half adder.</figcaption>
</figure>

So we have a success….we can now add any numbers up to…..2! Check closely, we can never have an answer of 3.

This isn’t much use. When you did binary in semester 1, you learned that to add two numbers, you need to be able to carry from one stage to the next. In the adjacent sum;

- 1 + 0 = 1 and no carry
- 1 + 1 + no carry = 0 carry the 1
- 1 + 1 + 1 carry = 1 carry the 1
- 1

Giving an answer of 1101

Our half-adder would work fine for the first calculation, where we can only add A and B. However, in the second calculation, we must be able to add A and B and the carry. What would a truth table for this look like?

I have built a (slightly more complex!) circuit in Cedar Logic to allow for a carry-in. What I have done in this case is to put two half adders together, one adds the two numbers to get the sum, the other adds the carry in to the sum to get a final sum.  Now we can add 1 + 1 + 1 to get 3!

<figure>
<img src = "https://jor-donegal.github.io/Background26/images/fig17.jpg">
<figcaption>fig 17. A full adder.</figcaption>
</figure>

Take a look at the truth table. 

<figure>
<img src = "https://jor-donegal.github.io/Background26/images/table3.jpg">
<figcaption>Table 3. Full adder addition, truth table.</figcaption>
</figure>

Finally, do a little reading on _twos complement_ in binary, we can use that technique in maths to do subtraction. 

I have created a simple circuit using four full adders which adds two four bit numbers in the normal way as A + B. However if I turn on the subtract switch, it adds one (by connecting to the carry in) and inverts the B bits giving the sum A-B. 

<figure>
<img src = "https://jor-donegal.github.io/Background26/images/fig18.jpg">
<figcaption>fig 18. A four bit adder.</figcaption>
</figure>

By using simple tricks and mathematical techniques, we can do complex manipulation with very simple circuits.

This may not seem very impressive, but remeber the first microprocessor was the Intel 4004, __a four-bit processor!__

