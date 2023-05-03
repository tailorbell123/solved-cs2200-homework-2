Download Link: https://assignmentchef.com/product/solved-cs2200-homework-2
<br>
<span class="kksr-muted">Rate this product</span>

<table>

 <tbody>

  <tr>

   <td></td>

   <td></td>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

   <td></td>

   <td></td>

  </tr>

 </tbody>

</table>

In this problem, you will be introduced to the 16 bit LC (Little Computer) 2200 assembly language. You will learn the syntax and semantics that underlie each of the supported operations. Although our instruction set is not as extensive as MIPS (Microprocessor without Interlocked Pipeline Stages) or x86, it is still able to solve a multitude of problems. In a LC-2200 computer, the word size is two bytes (16 bits), and there are 16 registers. We restrict memory to be addressable by words.

Register Conventions

Although the registers are for general-purpose use, we shall place restrictions on their use for the sake of convention and all that is good on this earth. Here is a table of their names and uses:

Table 1: Registers and their Uses

Register Number

Name

Use

Callee Save?

<pre>0123456789101112131415</pre>

$zero $at $v0 $a0 $a1 $a2 $t0 $t1 $t2 $s0 $s1 $s2 $k0 $sp $fp $ra

Always Zero Reserved for the Assembler Return Value Argument 1 Argument 2 Argument 3 Temporary Variable Temporary Variable Temporary Variable Saved Register Saved Register Saved Register Reserved for OS and Traps Stack PointerFrame Pointer Return Address

NA NA No No No No No No No Yes Yes Yes NA NA Yes No

Register 0 This register is always read as zero. Any values written to it are discarded.Register 1 is a general purpose register, you should not use it because the assembler will use it in

processing pseudo-instructions.Register 2 is where you should store any returned value from a subroutine call. Registers 3 to 5 are used to pass arguments into subroutines.

Registers 6 to 8 are used to store temporary values. Note that registers 2 through 8 should be placed on the stack if the caller wants to retain those values. These registers are fair game for the callee (the subroutine) to trash.

Registers 9 to 11 are the saved registers. The caller may assume that these registers are never tam- pered with by the subroutine. If the subroutine needs these registers, then it should palce them on the stack and restore them before they jump back to the caller’s code.

<table>

 <tbody>

  <tr>

   <td></td>

   <td></td>

   <td></td>

   <td></td>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

   <td></td>

   <td></td>

   <td></td>

   <td></td>

  </tr>

 </tbody>

</table>

<table>

 <tbody>

  <tr>

   <td></td>

   <td></td>

   <td></td>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

   <td></td>

   <td></td>

   <td></td>

  </tr>

 </tbody>

</table>

<table>

 <tbody>

  <tr>

   <td></td>

   <td></td>

   <td></td>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

   <td></td>

   <td></td>

   <td></td>

  </tr>

 </tbody>

</table>

<table>

 <tbody>

  <tr>

   <td></td>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

   <td></td>

  </tr>

 </tbody>

</table>

HW 2 Question 4 CS 2200 – Systems and Networks Fall 2017

Register 12 is used to handle interrupts (something we’ll get to in a few weeks).Register 13 is your anchor on the stack. It keeps track of the top of the activation record for some

subroutine.

Register 14 is used to point to the first address on the activation record for the currently executing process. You do not need to worry about using this register.

Register 15 is used to store the address a subroutine should return to when it is finished executing. It is only supposed to be used by the JALR (Jump And Link Register) command.

Instruction Formats

There are four types of instructions: R-Type (Register Type), I-Type (Immediate value Type), J-Type (Jump Type), and S-Type (Special Type).

Here is the instruction format for R-Type instructions (ADD, NAND):

Here is the instruction format for I-Type instructions (ADDI, LW, SW, BEQ):

Here is the instruction format for J-Type instructions (JALR):

Here is the instruction format for S-Type instructions (HALT):

Symbolic instructions follow the same layout. That is, the order of the registers and offset fields align with the order given in the instruction format, ie. instructions in assembly are written as:instruction RX, RY, RZ orinstruction RX, [optional offset](RY).

Bits

15 – 13

12 – 9

8-5

4-1

0

Purpose

opcode

RX

RY

RZ

Unused

Bits

15 – 13

12 – 9

8-5

4-0

Purpose

opcode

RX

RY

2’s Complement Offset

Bits

15 – 13

12 – 9

8-5

4-0

Purpose

opcode

RX

RY

Unused (all 0s)

Bits

15 – 13

12 – 0

Purpose

opcode

Unused (all 0s)

<table>

 <tbody>

  <tr>

   <td></td>

   <td></td>

   <td></td>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

   <td></td>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

   <td></td>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

   <td></td>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

   <td></td>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

   <td></td>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

   <td></td>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

   <td></td>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

   <td></td>

   <td></td>

   <td></td>

  </tr>

 </tbody>

</table>

<table>

 <tbody>

  <tr>

   <td></td>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

   <td></td>

  </tr>

 </tbody>

</table>

HW 2 Question 4 CS 2200 – Systems and Networks Fall 2017

Table 2: Assembly Language Instruction Descriptions

Name

Type

Syntax

Opcode

Action

add

R

add RX, RY, RZ

000

Add contents of RY with the contents of RZ and store the result in RX.

nand

R

nand RX, RY, RZ

001

NAND contents of RY with the con- tents of RZ and store the result in RX.

addi

I

addi RX, RY, immval5

010

Add contents of RY to the contents of the immval5 field and store the result in RX.

lw

I

lw RX, offset5(RY)

011

Load RX from memory. The memory address is formed by adding the offset to the contents of RY.

sw

I

sw RX, offset5(RY)

100

Store RX into memory. The memory address is formed by adding the offset to the contents of RY.

beq

I

beq RX, RY, target

101

Compare the contents of RX and RY. If they are the same, then branch to ad- dress PC + 1 + offset, where PC is the address of the beq instruction. Mem- ory is word addressed. Note that if you use a label in a BEQ instruction, it will jump to the relative offset of the label. If you specify a label, the assem- bler will calculate the offset for you.

jalr

J

jalr RX, RY

110

First store PC + 1 in RY, where PC is the address of the jalr instruciton. Then branch to the address in RX. If RX = RY, then the processor will store PC + 1 into RY and end up branching to PC + 1.

halt

S

halt

111

Halts the processor and discontinues ex- ecuting further instructions.

LC 2200 provides a number of pseudo-instructions.Table 3: Assembly Language Pseudo-Instructions

Name

Example

Action

la

la $a0, MyLabel

Loads the address of a label into a reg- ister.

noop

noop

No operation, does nothing. It actually does add $zero, $zero, $zero.

.word

.word 32, .word MyLabel

Fills the memory location it is located with a given value or the address of the label.




Play around with the simulator. Try writing some simple programs to copy values from one register to another or to load/store values from memory. You should get familiar with the syntax for the assembler.

When you extract the archive, you will have access to an assembler (assembler.py), a python file that defines the ISA for the assembler (lc2200hw1-isa.py), and a simulator (lc2200hw1-sim.py). The assembler and simulator run on any version of Python 2.6+. Here is the suggested workflow for writing and running your assembly programs on the simulator:

<ol>

 <li>Edit and save your assembly file with your favorite text editor.</li>

 <li>Assemble your code via the assembler. The command below will generate a file called myFile.bin by using a myFile.s assembly file and the ISA for this homework:<pre>     python assembler.py -i lc2200_16-isa --sym myFile.s</pre></li>

 <li>You can run your .bin file with the simulator by typing python lc2200_16-sim.py myFile.bin. Some useful commands are ‘r’ for run, ‘q’ for quit, ‘break [line # or label]’, and ‘help’.</li>

</ol>

Exercise: Fibonacci Test Program

In this problem, you have to use the LC 2200 assembly language to write a simple program.

Write a function in LC-2200 to compute fibonacci(num). Your implementation must be recursive and follow the LC-2200 calling convention introduced in lecture. For a review of the calling convention, see the “LC-2200 Calling Convention” slides under Resources on T-Square.

You may find the following pseudocode helpful:

fibonacci(n) = fibonacci(n − 1) + fibonacci(n − 2) fibonacci(0) = 0 and fibonacci(1) = 1

Purely iterative implementations will receive no credit. Points will be deducted for not following the calling convention correctly.

NOTE: Your function should work for any n ≥ 0. You do not have to handle detecting integer overflow. When your program exits, the result should be in the $v0 register.

Hints

<ul>

 <li>We recommend starting with a solution in a higher level language such as C, and then moving to assembly.</li>

 <li>Comment your code. Assembly is hard to read, and comments aid in debugging while providing clarity.</li>

 <li>When you make a recursive call, you will have to overwrite the current arguments stored in the $a0-$a2 registers. If you need to access those again, you can either (1) treat them like $t registers and push them to the stack, or (2) copy the arguments into local variables or $s registers.Feel free to ask us questions in our office hours, on Piazza, or in the weekly recitation. Make sure that fib.s is in a UNIX-readble format (no DOS/Windows nonsense).DeliverablesTurn in the following files to T-Square:• fib.s, which has your assembly code.Be sure to put your name in a comment at the top of the file.The TAs should be able to type python assembler.py -i lc2200_16-isa –sym fib.s and then lc2200_16-sim.py fib.bin to run your code. If you cannot do this with your submission, then you have done something wrong.</li>