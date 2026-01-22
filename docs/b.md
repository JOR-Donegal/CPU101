# Logic Gates
Once we have basic components, we can build for complex circuits, _logic gates_.

The study of logic goes back (at least!) to our earliest cultural origins; the Arabs, Greeks, Chinese and Indians all had advanced concepts which were the origin of our modern science.  In modern computer science and mathematics, we trace our reasoning back to Aristotle and the early Greek mathematicians, as we strove to formally describe reasoning, arguments and proofs in an unambiguous mathematical language. The term logic itself comes from the Greek λογική logikē or the study or arguments. 

Some of the most important work in logic (in fact the basis of modern computer theory) was carried out by George Boole at UCC from 1849. Boole established the system now known as Boolean algebra, where variables are truth values true or false. The device which we based our electronic revolution on was the transistor; electronic switches which could have the values on or off. Boolean algebra was ideally suited to this binary environment has been fundamental to our development of digital logic, modern electronics, and eventually computing. In the 1930’s, Claude Shannon applied Boolean algebra to circuits built using switches, providing the foundations for modern computing.

Boolean expressions are normally true or false, or on and off, or 1 and 0, all are representations of the same thing. In any system, we can have Boolean variables which can contain a Boolean expression. 

Boolean operators let us look at the relationship between the state of these variables and an output. Let’s go with variable C for an output.  We know that if A is on (true) and B is on (true) then the machine is safe and C should be equal to on (true) But look at all the possible cases that give rise to an output. We call this a truth table; it allows us to look at all possible inputs and have a predictable and desired output. 

<figure>
<img src = "https://jor-donegal.github.io/CPU101/images/fig1.jpg">
<figcaption>Fig 1. An AND gate, truth table and symbol.</figcaption>
</figure>

In logic terms, IF A AND B THEN C. 

This behaviour is the Boolean operator __AND__. This is formally represented by the symbol and truth tables shown in Fig 1. By convention, we show our Boolean expressions as 1 and 0, the binary levels used in both digital logic and in computing.

The second Boolean operator we will consider is the OR gate, Fig 2. In this case if either input A or input B is equal to 1 (true) then the output of the gate will be 1 (true).

The output is 0 (false) only when both inputs are 0 (false).

<figure>
<img src = "https://jor-donegal.github.io/CPU101/images/fig2.jpg">
<figcaption>Fig 2. An OR gate, truth table and symbol.</figcaption>
</figure>

In electronics, we may sometimes buffer an input from an output. This is done for a range of reasons, mostly to reduce the electrical load on a circuit.  

The triangle symbol on its own means it’s just a buffer, it does not change the Boolean value at its input to anything different at the output.

<figure>
<img src = "https://jor-donegal.github.io/CPU101/images/fig3.jpg">
<figcaption>Fig 3. A buffer, truth table and symbol.</figcaption>
</figure>

Sometimes we need a logic function which just inverts a Boolean variable. For example if we have a 1 and we need a 0, or vice versa. We refer to this as a NOT function.

We can signify this in a few different ways. We can use any standard logic symbol with a circle on the output. The circle denotes an inversion.  Alternatively, we can put a bar over the variable symbol; a bar over A means NOT A. 

<figure>
<img src = "https://jor-donegal.github.io/CPU101/images/fig4.jpg">
<figcaption>Fig 4. An inverter, truth table and symbol.</figcaption>
</figure>

We can apply the same sort of approach to other logic gates. For example a NOT AND gate is a NAND gate. It has the same truth table as an AND gate, except with the output inverted. Similarly a NOT OR gate is called a NOR gate.

<figure>
<img src = "https://jor-donegal.github.io/CPU101/images/fig5.jpg">
<figcaption>Fig 5. NOR and NAND, truth table and symbol.</figcaption>
</figure>

The final Boolean operator we need to look at is the exclusive OR (XOR) gate. This is a special case or the OR gate where the output is 1 if either input is 1, but is 0 is all inputs are 1. Obviously we can also have an XNOR, which is an XOR with the output inverted. 

<figure>
<img src = "https://jor-donegal.github.io/CPU101/images/fig6.jpg">
<figcaption>Fig 6. XOR and XNOR, truth table and symbol.</figcaption>
</figure>

In early digital systems (c. 1950) we actually built logic gates out of transistors, resistors and other discrete components. 

By the 1960’s we had integrated these transistors into single chunks of silicon we called integrated circuits or IC’s. This allowed for the next revolution in computing, which allowed us to get a CPU onto a single large circuit board. These early silicon chips used _transistor-transistor logic_ (TTL) and can be recognised by a 74xxx prefix. 

For example, a 7400 was a package with 14 legs which had four NAND gates inside.

<figure>
<img src = "https://jor-donegal.github.io/CPU101/images/fig7.jpg">
<figcaption>Fig 7. 7400 TTL.</figcaption>
</figure>

In later circuits, the 74xxx series were superceeded by 4xxxx series, using CMOS transistors and lower power.

Based on the availability of the early silicon chips, computers began to be built which were commercially viable. The IBM 360 series revolutionised early computing using these kinds of technologies. Throughout the 1970’s mini-computers and mainframes were developed and the computing industry blossomed.

I still use these chips when designing and building simple prototypes.

Do some background reading and identify some circuits that use transistors to implement logic gates.