> [!Representation]
> Representation is how we use aspects of the physical word as a stand in for other aspects of the Physical World.

# Number Systems

>[!Tallies]
>For Example Lebombo Bone (only  for counting)
>> Grouping Tallies into groups of 5 makes it faster to count

>[!Tokens]
>Typed Counting and addition- Addition is slow n+m is O(n+m)

>[!Bulla]
>Clay scroll guaranteeing the number of tokens inside

>[!Roman Numerals]
>Evolved from tallies difficult to do complex arithmetic with

>[!Split Talies]
>Stock and Foil; wood is split into half "Stock and Foil". 
>> Evolved into Modern Stock Trading System

### Numerosity

- Humans directly percieve numbers around 1-5.
	- Then perceive only rough "Numerosities" around 10,20,50,100,100 etc
- Computers are not restrained by this restriction.
### Base Systems

> [!Decimal]
> The Decimal system is Base-10. n digits can store ${}10^n-1{}$ digits.
> Modern Computers do not understand the decimal system.
> >${}7 4 7 5 = 7\times10^3+4\times10^2+7\times 10^1+5\times 10^0{}$
>  

>[!Binary]
> Binary is Base-2 and is represented with *on* and *off* voltages
> n digits (or bits) can store ${}2^n-1{}$ values
>
>> 1110 (binary) = 14 (decimal)
>> ${}1110 = 1\times 2^3+1\times 2^2+1\times 2^1+0\times 2^0 = 14{}$
>
> You can multiply by 2 by shifting digits left (and divide by 2 via shifting right)
> ```C
> x = x >> 1 // shift right once to multiply the value of x by 2
> ```

>[!Sexagesimal]
>Sexagesimal is base 60. A Hybrid of base 10 and base 12.
>Modernly used for time and arcdegrees.
>again; n digits store ${}60^n-1{}$ values.

>[!Hexadecimal]
>Hexadecimal is Base-16 (plays nice with Binary as ${}16 = 2^4{}$)
>again... n digits can store ${}16^n-1{}$
>
>
>${}2 F 4 D = 2^16^3 + F (16) \times 16^2 + 4\times 16^1 + D(13)\times 16^0 = 12,109{}$
>
>We use Hex to store colours, and easily read/ convert binary values

> [!Base-256 (Bytes)]
>n bytes can store ${}256^n-1{}$ values
>1 byte is written as 2 hex codes (or 2 Nybbles!) (Or 8 Bits)
>Plays nicely with Hex and Binary

>[!Base b]
>Any number "b" can be used as a base.
>Again n digits can store ${}b^n-1{}$ values.

>[!Heirarchy of Chomps]
>Bit - 1 Bit
>
>Nybble - 4 Bit
>
>Byte = 8 Bit
>
>Word = "Natarul Unit for a given CPU" -> Usually 64 bits on a modern 64 Bit CPU.

Base can be represented in subscript ${}Binary = 1110_{2}{}$, ${}Hexadecimal = 2D_{16}{}$ etc

## Binary Addition

0 + 0 = 0

0 + 1 = 1

1 + 0 = 1

1 + 1 = **1**0

### Integers

>[!Signed Binary]
>Signed Binary use the first bit of your number to define the sign
>0 = +
>1 = -
>
>This reduces the total number of values you can represent with binary.

>[!Ones Complement]
> If Your Number is negative; Invert all Bits; 001101 -> 110010
> 
> Not a real world system

>[!Twos Complement]
>If Your Number is Negative; Complement and add one; 001101 -> 110011

- Sign and One's Compliment both make an unreal -0 number; Hence why they are not used

>[!Subtraction]
>Using Twos Compliment You never need to do subtraction> Just add the twos compliment of the number you are subtracting.
>
>1101 - 1001 (13-9)
>Perform twos compliment on 1001
>1101+0111 = 10100 (carry bit ignored) = 0100 (4)

One byte can store Natural numbers between 0 and 255, or signed integers between -128 and 127.

One 16 bit word can store Natural numbers been 0 and 65,525, or signed integers between -32768 and 32767

Natural numbers are often called unsigned.

### Rational Numbers

Aka Fractions

In general can be represented as ${}\frac{a}{b}{}$ where a and b are integers. 

Fractions are a simple example of a data structure (storing 2 integer types). 

However, it is over-complete (2 numbers represent the same number) for example:
${}\frac{4}{8}=\frac{1}{2}{}$

### Floating Point

we can approximate real numbers (numbers with decimals) with floating points

s = significand (defines precision)
e = exponent (defines range)

${}3.14\times 10^0=314\times 10^{-2}{}$

>[!Example]
>IEE 754 Standard 64-bit
>1-bit sign
>11-bit exponent
>53-bit significand
>Codes for +inf, -inf and NaN (Not a Number)
> ---
> Half Precision FP16
> 1-bit sign
> 5-bit exponent
> 10-bit significand
> Codes for +inf, - inf and NaN (Not a Number)
> ---
>Half Precision BF16 (Brain Float)
>1-bit sign
>8-bit exponent
>7-bit significand
>Codes for +inf, -inf and NaN (not a Number)

### Computable Numbers

Turing Numbers (Computable Numbers); 
- A computable subset of classical Real Numbers
- Whose *n*th digit can be obtained by a finite program

# Text Systems

Text began as Pictograms (ie Hieroglyphics) this later evolved in Cuneiform's in Sumeria; Later Runes in Northern Europe, which became Symbolic Languages like Chinese.

Later alphabetical systems evolved.

Braille and Morse-code are proto-binary representations of text.

### ASCII

American Standard Code for Information Interchange.

- From 1960s
- Represents each character as a unique 7 bit code.
- 128 Characters available

- fit in one Byte aka one "char"
	- The extra bit later became very useful
- Everything on a typewriter was repented by a binary code; including delete key, enter, etc.

### Unicode (UTF)

- From 1991: Generalisation of ASCII codes
- More than 1 million different characters

- 150+ Alphabets represented, including emojis....

UTF-8:1-4 bytes, starting with 0 is just Ascii
UTF-16: 2-4 bytes
UTF-32: fixed 4 byte width.

# Data Structures (Media Systems)

```C
struct Employee {
int id;
chat Name[10]
float salary
}
```
  Structs can be used to store multiple pieces of data.
  e.g Lists, images, audio, video etc.

### Images

RGBA is 32 Bit, Red, Green, Blue and Alpha (in 3D array)

### Audio

Represented as a series of integers

### Video

Many Images in series - Can be compressed by only changing the difference

### Multi Media Streams

Contains Video, Audio, Text etcetcetc.