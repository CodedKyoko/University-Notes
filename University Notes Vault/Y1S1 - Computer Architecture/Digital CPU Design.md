# CPU Function

"User facing"; The function of the CPU is to run programs in binary.

1 and 0's are equivalent to punch cards, a sequence of "on" and "off" to tell the computer what to do.

The first 2 bits are opcode, the other bits are operands.

## FDE ( Fetch Decode Execute )

## Fetch

"Fetching" the next instruction to execute:
Program Counter gives you the address of the next instruction; go to it and bring it back to the CPU (stored in the instruction register) (from memory).

## Decode

Decode converts the opcode into switching on some circuit (from the instruction register into the control unit)

## Execute

Execute.. executes the binary instruction (no matter what, for example loading and storing data from/ too the memory across the data bus).

Other types of instructions can be arithmetic using the ALU, 

>[!Note]
>In Harvard Architecture (like the Analytical Engine), Programs and Data have seperate address spaces.
>In Von Neumann Architecture they share a single space, so LOAD and STORE can access the program as data.

# Registers

The CPU Has many internal registers; Registers are just a sequence of flip flops storing one bit of data each.

## Internal Register

Registers not available to the programmer to modify.

### Program Counter

Address of the instruction

### Instruction Register

Automatically incremented after each fetch-execute cycle

## User Visible/ Facing registers.

Programmer accessible registers

### Accumulator

## ALU (Arithmetic Logic Unit)

The ALU performs addition, subtraction, multiplication, division, logical operations and binary shifts.

- Input: Data (a, b) ; operation type (c)
- Output: Result of operation (r) ; status flags of operation (f, carry, overflow, etc)

## CU (Control Unit)

The CU coordinates activities of the CPU; Instruction fetching and decoding, execution management, timing. 

Driven by a clock, a number of clock cycles is require to carry out each data movement or a computational operation. 

Implemented in Digital logic.


# Control Flow

## Branching

Branching changes the sequence of execution
- making decisions
	- Conditional (IF) statements : e.g. if a number is zero or positive perform the square root calculation, report an error otherwise
- Repetition of certain parts of code
	- e.g. loops (FOR, WHILE, Etc)
- Breaking up code into smaller parts
	- Subroutines, functions, methods

### Unconditional Branch

E.g JUMP Z

Z: Address of the next instruction

Write Z to program counter

(like a function)

### Conditional Branch

Jump (to location) if a specific condition has occurred

example: 
if statement
loops
etc

- if the overflow flag after the last operation == 1; do this.

>[!Styles]
>Jump Style:
>Compare X TO 0
>Branch on equal 100 (If equal, jump to line 100)
>carry on...
> ---
>Skip Style:
>Compare X TO 0
>SKIPCOND (If Equal, skip next line)
>JUMP 100 (Jump to line 100)
>carry on ...


