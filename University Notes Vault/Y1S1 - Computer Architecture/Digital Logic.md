# Switches

## Transistors

Transistors are a switching element "if x then make y happen". Made of Silicon.

### Integrated Circuit

Also known as a "Microchip" or "Chip". Built from a number of Transistors

>[!One Way Physics]
>Transistors are one way - This is very difficult as physics is 2 ways.
>>[!Example]
>>Water Valves are a common example for water. Water can push open the valve in one direction, but cannot push open the valve the other way.
>
>>[!Note]
>>In real computers we use Semiconductors, Semiconductors are elements which "Nearly" conduct, typically; Silicon (element-14). Half full outer shell, lattice shares electrons to fill shells. (Covalent Bonding)
>

### Diodes

Diodes are the electronic equivalent of the water valve,
we "Dope" half the diode, called the n region, with larger atoms (e.g Aluminium (15)). and "Dope" the other half the p region, with smaller elements, e.g element 13. 

- This creates a Balance
	- Chemical Force: Wants full shells
	- Electrical Forces: Want neutral charge

This makes it so that electricity will only flow in one direction from the "n region" to the "p region".

When the diode is "closed" a "Depletion zone" forms between the n and p region; Which emits energy as heat and light.

>[!Creating Transistors]
>
>To create a transistor you can put 2 diodes back to back called "pnp" Injecting current into the n region, and pushing current from p to n, will create a current out of the collector.
>Without the injected current it will not be able to conduct electricity in either direction.

### Transistor Fabrication

Similar circuits as 1940's patch wires in the ENIAC

Roughly 300 steps.

Stages can be subtractive or additive.

#### Photolithography

Costs 0.5 billion USD per machine, can print transistors at 2nm scale.

Prints patterns on a silicon wafer using a mask.

#### 3D printing

Copper wires and Silicon (+ dopants) Transistors are 3-D printed.

## Logic Gates

Logic gates are an electronic device capable of performing "Logic Functions" (OR, AND, XOR, NOT etc).

One or more logic input in some representation

One or more logic outputs in **exact same representation**

>[!Example]
>Coded boolean values as voltage, e.g 0V = False, 5V = True.

#### AND

Input 1 AND input 2 must be true for the output to be true


| Input 1 | Input 2 | Output |
| ------- | ------- | ------ |
| 0       | 0       | 0      |
| 0       | 1       | 0      |
| 1       | 0       | 0      |
| 1       | 1       | 1      |

#### OR

Input 1 OR Input 2 can be true for the output to be true

| Input 1 | Input 2 | Output |
| ------- | ------- | ------ |
| 0       | 0       | 0      |
| 1       | 1       | 1      |
| 1       | 1       | 1      |
| 1       | 1       | 1      |

#### NOT

True input makes false output

| Input | Outout |
| ----- | ------ |
| 0     | 1      |
| 1     | 0      |

#### XOR

Input 1 OR input 2, only one an eb true for the output to be true

| Input 1 | Input 2 | Output |
| ------- | ------- | ------ |
| 0       | 0       | 0      |
| 1       | 1       | 1      |
| 1       | 1       | 1      |
| 1       | 1       | 0      |

#### NAND

AND gate with inverted output

| Input 1 | Input 2 | Output |
| ------- | ------- | ------ |
| 0       | 0       | 1      |
| 1       | 1       | 1      |
| 1       | 1       | 1      |
| 1       | 1       | 0      |

#### NOR

OR gate with inverted output

| Input 1 | Input 2 | Output |
| ------- | ------- | ------ |
| 0       | 0       | 1      |
| 1       | 1       | 0      |
| 1       | 1       | 0      |
| 1       | 1       | 0      |

### Universality

NOR And NAND are Universal, they can be used to make any machine

### Making Logic Gates

- Modern "Chips" (Microprocessors) are made form Transistors.
	- Electrical "circuits" only exist at this  level.
- But designers think in terms of gates.

You must use a more complex circuit for AND / NAND instead of just using one transistor, to maintain the quality of the signal.

## Boolean Logic

Boolean logic is the basis of all computation, you can stack many many Logic gates together to make any machine using Boolean Logic (Also the basis for the boolean/ bool datatype.)

Truth Values: Values can only be True or False.

#### Logic as Arithmetic

Let 0 = False, 1 = True

Let AND = multiply, Or = add-without-carry

Let NOT x = 1-x (sometimes written x' or x)

Often used in older (Not ""sloppy"") programming languages, eg. C

But also a way to map binary arithmetic to logic.

#### Boolean Model Checking

comparing 2 boolean expressions by creating a full truth table for all the components of the expressions. The compare the tables; if the 2 expressions produce the same truth tables, then they are the same.

#### Boolean Identities

| Name             | AND Form                  | OR Form                   |
| ---------------- | ------------------------- | ------------------------- |
| Identity Law     | 1 A = A                   | 0 + A = A                 |
| Null Law         | 0 A = A                   | 1 +A = 1                  |
| Idempotent Law   | A A = A                   | A + A = A                 |
| Inverse Law      | A !A = 0                  | A + !A = 1                |
| Commutative Law  | A B = B A                 | A + B = B + A             |
| Associative Law  | (A B) C = A (B C)         | (A + B) + C = A + (B + C) |
| Distributive Law | A + B C = (A + B) (A + C) | A (B + C) = A B + B C     |
| Absorbtion Law   | !A (A + B) = A            | A + A B = A               |
| De Morgans Law   | !A !B = !A + !B           | !A + !B = !A!B            |

# Simple Machines

Connecting gates together can create more complicated components. Combinations of gates implement boolean functions.

If we can simply the Boolean expression (via model checking or boolean identities) then we can create simpler circuits. (cad software can also do this automatically)

>[!Multi Input gates]
>Multi input gates can take more than 2 inputs, allowing you to "generalise" AND or OR operations. (Reduce the number of AND and OR gates that you use)

### Shifter

- Move the input bits left or right (multiply or divide binary number by 2).

Logical shift right = divide by 2.
`z = x >> 1;`
Logical shift left = multiply by 2
`z = x <<1;`

### Decoder

- has n input lines that determine which one of the 2n output lines is selected

- Used to decode CPU instructions; Roughly equal to assembly commands; used to pass signals to ALU/execution circuits

### Multiplexer

- Selects one output from multiple inputs (using similar logic to the decoder)

- Connects all outputs to one shared final output.

### Adder

Adders, as the name implies performs addition (and hence subtraction, multiplication etc).

#### Half Adder

A Half adder can add up 2 digits, and returning 2 digits

- The sum can be found using the XOR operation, the carry using the AND operation.

Truth Table:

| X   | Y   | Output (XOR) | Carry (AND) |
| --- | --- | ------------ | ----------- |
| 0   | 0   | 0            | 0           |
| 0   | 1   | 1            | 0           |
| 1   | 0   | 1            | 0           |
| 1   | 1   | 0            | 1           |


#### Full Adder

A full adder is capable of adding up to 3 digits and returning 2 digits

A Full Adder can be made by stacking 2 half adders together, and putting their carries into an OR Gate.

Turth Table:


| X   | Y   | C-In | Output | Carry |
| --- | --- | ---- | ------ | ----- |
| 0   | 0   | 0    | 0      | 0     |
| 0   | 0   | 1    | 1      | 0<br> |
| 0   | 1   | 0    | 1      | 0     |
| 0   | 1   | 1    | 0      | 1     |
| 1   | 0   | 0    | 1      | 0     |
| 1   | 1   | 0    | 0      | 1     |
| 1   | 1   | 1    | 1      | 1     |
We can represent the full adder as a single symbol, as its a very common logic circuit

You can stack many full adders together to do multi bit addition

>[!Note]
>All of the logic we have seen so far is "Combinatorial"
>- Output depends directly on input valves
>- Good for signal routing (decoding, multiplexing)
>- Good for arithemtic (adders)
>- No possibility for storing data = cannot make a computer

## Sequential Logic

Feedback: Connecting a gates output to its input

e.g x(t+1) := NOT x(t)

Non Paradoxical (Self referential) because of time

Feedback is used to retain the signal value

| A   | Prev. State | Current State |
| --- | ----------- | ------------- |
| 0   | 0           | 0             |
| 1   | 0           | 1             |
| 0   | 1           | 1!            |
| 1   | 1           | 1             |
^^ Piping the output of an OR gate back into its input.

Not ideal for memory as it cannot be taken back to 0 from 1.

### Synchronisation (with a clock)

- State changes need to occur in a sequence
- controlled by clock
- physical oscillator, e.g quartz crystal
- produces electrical waveform's which act as "ticks"
- frequency = cycles/time e.g. MHz, GHz
- Most digital components have an additional clock input
- usually the trigger is the positive/ leading edge (posedge)


| S   | R   | Prev. State | New State |
| --- | --- | ----------- | --------- |
| 0   | 0   | 0           | 0         |
| 0   | 0   | 1           | 1         |
| 0   | 1   | 0           | 0         |
| 0   | 1   | 1           | 0         |
| 1   | 0   | 0           | 1         |
| 1   | 0   | 1           | 1         |
| 1   | 1   | 0           | -         |
| 1   | 1   | 1           | -         |
This is a "flip flop" - Like a minecraft S R Snorlach, or T flip flop

R is for "reset" when you put a 1 into the circuit it stays as 1 forever, until R = 1, then it becomes 0.

(There are a lot of different types of flip flops)

Once we have this, we can make more complicated things, like a 4 bit counter or accumulator. (and just registers in general tbh)


