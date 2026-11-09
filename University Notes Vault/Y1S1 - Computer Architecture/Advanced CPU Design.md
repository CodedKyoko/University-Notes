# Instruction Set Design

A complete collection of instructions understood by some CPU
- Machine Code (Binary)
- Usually represented by ASM
- Human or compiler programming API

Often what is meant by "an architecture" (amd64, RISC-V, Ada Lovelace, blackwell, Redstone, Rubin, etc)

>[!TradeOf]
>Needs to enable fast implementations. (But also need to be usable by users).
>- ISA design is the hardware software interface.
>- used to be for human programmers -- now for compilers. (And human compiler writers)

### Decisions...

>[!Number of USER Registers]
>- Accumulator Architecture: Single user register
>	- No need to specify all operands
>	- Single Accumulator (A) is implied, E.g ADD &0F8D
>	- Like many calculators: +5 means A:=A+5
>- Multi-Register architectures
>	- Multiple instructions forms or operands specity which ones.
>		- LDX &0F8D           # 6502: load from address to register X
>		- ADD R1, R2, R3     # RISC-V: r1:=r2+r3
>	- May also have an accumulator
>		- A common convention is that all results are stored in it
>		- ADD R1 R2             # A <- R1+R2

>[!Different Addressing Modes]
>Consider Different ways to express A = A + B
>Operands can be registers, addresses, numbers, indirection's....
>- ADD R1 R2    # Add value in register R2 to value in Register R1 store result in R1
>
>- ADD R1 Mem.Addr.50   # add value in address 50 to value in register R1 store result in R1
>
>- ADD R2 32 # Add constant 32 to register R2 store in R2
>
>- ADDI R2 &50   # Indirection: Add the value stored at the address which is stored at address 50 to R2 (used to implement pointers)
>
>- ADDO R2 &50 3   # Indirection with offset: Add the value in &53 to R2 (used for arrays).

>[!Arithmetic Instructions]
>What operations should be provided in software?
>
>- INC increment (+1)
>- DEC decrement (-1)
>- ADD
>- SUB
>- MULT
>- DIV
>- EXP
>- LOG
>- AND
>- OR
>- NOT
>- SHIFTLEFT
>- SHIFTRIGHT
>- COMPARE=
>- COMPARE!=
>- COMPARE<
>- COMPARE>
>- COMPARE<=
>- COMPARE>=
>  
>  More instructions use more silicone - but can make execution faster.
>  
>  Alternative is to write user programs for them from simpler ones.
>  
>  Most 8 Bit CPUs do not feature MULT, DIV, EXP, LOG etc

>[!Floating Point Architectures]
>E.g -1.343
>
>FP unit History:
>- FP Software Libraries
>- FPU Coproccessor chips
>- Now usually part of the CPU
>	- Implemented in digital logic
>	- Using an FP data representation
>	- "operation unit" grouping ALU, Logic ops, FPU
>- Dedicated FP registers and instructions
>	- Similar ideas to adders for ALU, but much much bigger and harder.
>	- 1194 Intel Pentium FP division bug, 0.5 bn USD loss.
>
> Including Floating Points is very hard and expensive
> 

# Subroutines

>[!Examples]
>- Procedure:
>	- Code that does something without returning
>- Function:
>	- Code that does something and returns a value
>- Method
>	- Mule crossbreed
>
>^ all Implemented as sub routines
>

A self contain piece of code which can be called from the main program.

• JSR and RTS (6502)
• CALL X and RET (x86)

Similar to jumps but this time the CPu has to know where to jump back too -- Return address
- So it can carry on from where it was before the call.
- Return address is the current value of the PC

PC return address may be stored:
- At an agreed location between caller and callee (Limits Recursion)
	- In a special CPU register,
	- At an arbitrary address in memory
	- in an address at the start of the subroutines code.

- On a stack (allows recursions, most common approach) <- Refer to [[Collections]]
	- Dedicate some area of memory for the stack
		- Stack overflow if it overruns into rest of memory
	- CPU stack pointer register (SP)
	- CPU push, pop instructions
		- e.g. PHA: Push accumulator to stack
		- Auto increment. decrement SP
	-  <- Stack and Heap????

>[!Interrupt Requests (IRQ)]
>- Interrupt: signal to jump out of usual control structure and do something else:
>	- Exception handling (e.g division by 0)
>	- OS functions
>- Implementation:
>	- Physical wires into CPU ("IRQ Lines")
>	- Plus special instructions:
>		- Set addresses to JUMP to on IRQ
>		- e.g Storing special register/s

### CPU Access Modes

>[!CPU Privileged Mode]
>
>Used only by Operating System Kernel
>	e.g Linux, BSD, MacOS, Windows etc.
>Can load/store from/ to all memory

>[!CPU Restricted Mode]
>For user programs
>Per-process Virtual Addresses

>[!Kernel Code]
>- On boot: Set up Timer and IRQ table calls
>- On Callback (<- From IRQ table called by Timer):
>	- Switch to privileged mode
>	- Copy user programs register states to RAM
>	- choose another user program
>	- load its saved state to registers
>	- switch to restricted mode
>	- fetch from PC (-> User Program)

>[!User Program]
>Load/Store only from.to own virtual addresses
>Gets interrupted by timer IRQ after running for a while

^^ Important for OS module (Depends on IRQ and Access modes lots)

# Instruction Level parallelism

## Register Parallelism

- Primary school/ abacus serial adding algorithm: O(n) time, O(n) work, n = # digits
	- In digital logic (e.g. Part of the ALU: called a ripple carry adder)
		- e.g seen in Pascals Calculator.
- Parallel adding algorithm (for teams): O(log n) time; O(n) work; n = # digits
	- How often do carries occur?
		- About 1/4 of casses? when both digits are "high"
		- also consider when digit has recieved a carry itself
		- Most natural quantities contain statistically low proportion of high valued digits
	- In ALU digital logic: called a carry save adder

Babbage tried to make a carry save style adder for the analytical engine.
> Same structure now seen in modern CPUs

## Pipe-lining

Manchester Baby is idle on most ticks. (as its not pipe-lined <- slow inefficient bad 3:)

Perform fetch, decode, execute for a series of different instructions on same ticks.

Like a production line 
e.g. 4 workers at once doing
- Fetch
- Decode
- Execute
- Write back
Instead of 1 worker doing them 1 at a time

Different architectures allow different pipeline stagings  
- number of stages grew c.1990-2000  
- then no obvious trend, grow+shrink  
- Intel recently has ~37 stages

>[!Warning] Hazard: Branching
>
>If the instructions branch (get changed) midway through execution you're going to have issues lol.

>[!Warning] Hazard: Data
>
> If 2 parts of the pipeline try to write to the same data location; your going to have issues.

>[!Warning] Hazard: Structure
>If 2 parts of the pipeline are trying to use the same register/ component at the same time; your going to have issues.

>[!Avoiding Hazards]
>
>Write Code to avoid it
>	- Avoid touching the same thing in nearby instructions
>Pipeline Stalling (bubbling)
>	- Inserting Null operations, NOPs, to delay things and avoid hazards
>Redoing Work
>	- Detect Hazards having happened, undo work, do again with NOPs
>Eager Execution
>	- Execute both possible branches at the same time
>	- Kill one when we know which is taken
>	  
>>[!Note]
>>"NOP" stands for No OPeration > It tells the CPU to do nothing for a while.

Flushing the Pipeline -> Means throwing away this execution of the pipeline due to a hazard and doing it again.

### Branch Predictors

- Most basic: Assume branch taken  
	- most branches are taken  
	- because most branches arise from loops and loops tend to loop many times before ending  
- Programmer or compiler hints  
- Dynamic (runtime) prediction based on:  
	- keep a log of what was done here last time or the last n times, and use probabilities many code features + neural networks in hardware…

### Operand Forwarding

Letting pipeline stages access intermediate results in-between other stages to see forward in time.
Requires lots of extra digital logic circuits.

## Out of Order execution

Often, programs can have instructions swapped with no change to the result

Clever swapping can reduce hazards and stalls - simple form of Data Flow Architecture
E.g. used in the RISC-V Berkeley Out Of Order Machine (BOOM, fully open source)

## Hyper Threading

Most of the CPU is idle; soooo use the idle parts to pretend to be a second CPU core; now you have 2 threads per CPU Core

# CISC v RISC

### CISC

CISC goal is to complete a task in as few lines of ASM as possible

Achieved by having many different instructions which each do complex specific things

>[!Advantages]
>- compiler has to do very little work to translate high level language into ASM
>- Length of ASM code is shorter - less ram used
>- Easy to ad custom instructions

Control units in CISC are very complex, and expensive to fabricate and test.

so we replace them with virtual machine units which allow us to upgrade the micro programs / microcode. Intel famously had a microcode issue that caused 13th and 14th gen chips to cook themselves.

microcode uses internal registers, hidden from the user.

The microcode uses simple commands, theoretically possible to change the microcode for an entirely different CPU

### RISC

RISC's goal is to be lower power and use simple instructions only "lean and mean"

Programmers need to code more RISC instructions per line of CISC instructions hence more RAM is needed to store these instructions, and the compiler has to work harder.

>[!Advantages]
>- Each instruction requires only one instruction cycle
>	- Smoothing pipel-ining
>- Easier to architect - less chances for bugs
>- *writing* the compiler is simpler
>- smaller size, lower power - great for anything that runs on a battery
>- No need for microcode