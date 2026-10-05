>[!Constants]
> Constants are used for variables that should not be changed, they can be created by adding the keyword "const" at the start of variable decleration:
> `const bool meow = true;`

>[!var]
>The `var` keyword can be used in place of a data type to tell the compiler we do not know the type of the variable yet:
>`var meow;`
> Can later be assigned as any data type (Via implicit conversion) (once).

## Numeric

### Byte

- 1 Byte in size
- Unsigned
- Minimum 0
- Maximum 255

### Sbyte

- 1 Byte in size
- Signed
- Minimum -128
- Maximum 128

### Short

- 2 Bytes in size
- Signed
- -32,768
- 32768

### Ushort

- 2 Bytes in size
- Unsigned
- 0
- 65,536

### Int

- 4 Bytes in size
- Signed
- -2 billion
- 2 billion 
  
### Uint

- 4 Bytes in size
- Unsigned
- 0
- 4 billion

### Long

- 8
- Signed
- HUGE NUMBER
- HUGE NUMBER
  
### Ulong

- 8
- Unsighned
- 0
-  HUGER NUMBER
  
### Float

- 4
- Signed
- 7 DIgits (floats the decimal point)
- Can store Decimals

### Double

- 8
- Signed
- 16 Digits (floats the decimal point)
- Can store Decimals

### Decimal

- 16
- Signed
- 29 Digits
- Can Store Decimals

> [!Scientific Notation]
> This is simple stupid simple, big or small numbers can be represented as powers of e; which is a short hand for 10
> 1.5e6 = ${}1.5\times10^{6}{}$

## Character and Text

### Char

- Enclosed with ' '
- Used to store single Charachters

### String

- Enclosed with " "
- Used to store multiple Charachters

 > [!Escape Sequence]
 > Use a Backslash \ to make the compiler ignore special charachtes. (Like " ", @ $ etc. )
 > 
 > Additionally \ can be used to represent other things such as new lines with \\n
 > 
 > @ Can be used in a similar way to $; but instead makes the compiler ignore all special charachters

## Logical

### Bool

- A Boolean is either true (1) or false (0)
