# Processors
The only kind of program a _Central Processor Unit_ (CPU) can execute is one which has been written in _machine code_. This is a binary file, with a sequential list of instructions (or _opcodes_) and data (or _operands_). To view a machine code program, we need to use a hex editor, but whether we represent the program as hexadecimal or binary, it is just numbers. One of the ways we indicate that we are using hexadecimal is to prefix the number with 0x. For example, 0xAA is AA^16^ or 170~10~. Do some general reading; review some of the instructions used by a modern CPU.

Humans do not understand pages of numbers very well, so we created the lowest level programming language possible, one where every instruction in a processor’s instruction set has a shortcut name, which makes sense to humans. If we had a machine code instruction 0x05 and it was a command to add two numbers, we could give it a _mnemonic_ (or shortcut name) of __ADD__. Similarly, a machine code instruction 0xF7 to multiply two numbers might have the mnemonic __MUL__. We could write a full program in this _assembly language_, the mnemonics used in any instruction set. We could use an ordinary text editor to write this, and it would be human readable and understandable. Each instruction in this program would have a one-to-one correspondence with machine code instructions, so a program written in assembly language would be just as efficient as one written in machine code. One catch; the processor cannot understand an assembly language program.

To convert the text of an assembler program to executable machine code we need to _compile_ it with a dedicated program which is called a _compiler_. For clarity, most Windows users use the extension .asm to designate an assembly language file. The assembler file may also be referred to as _source code_. In the code example below, I create some variables and put numbers into two of them. I load one number into a register (EAX) and then add another number to the register. Finally, I store the contents of EAX into a variable called result.

```
section .data
    num1 dd 3        ; first number
    num2 dd 5        ; second number
    result dd 0      ; to store the sum

section .text
    global _start

_start:
    mov eax, [num1]     ; load num1 into EAX
    add eax, [num2]     ; add num2 to EAX
    mov [result], eax  ; store result

    ; exit program
    mov eax, 1          ; sys_exit
    xor ebx, ebx        ; status 0
    int 0x80
```

Building your own code in assembler is a bit like building a car from parts, it is very time consuming, very detailed. We want to take as much advantage as possible of the work we do. For that reason, in all programming languages, we tend to write our code in re-usable sections, called _procedures_ or _sub-routines_. We also use classes, but that is a different story for much later in this module.
We rarely use assembler; it is a slow and difficult way to code. Instead, we use high-level languages. These are languages which are easier and more efficient for humans to use. In this module, we may see variations on the C language, Python, and PowerShell.

When I am writing a project, I tend to use a very modular approach. Every time I need to do something I write the programme steps (or algorithm) as a single mini programme. I will also document this mini programme so that I can remember what it does the following year or in the case of some code I have written, the following decade\century\millennium!

A big application I wrote during the pandemic looked like two months coding but using existing functions and class libraries, I had an alpha version working in a day. In any programming language, I recommend that you keep a track of all the code you have developed and that you develop your code in a modular way. We keep code in repositories, and we will look at that approach later in the module.

The last time I wrote assembly professionally was in the early 1990s, I am competent to talk about it, but no longer to code in it!