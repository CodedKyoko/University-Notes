

## How to use C-Sharp / .NET (dotnet)

We run C# using dotnet `dotnet run` while in the project root. Its truly that simple (worse build tools than cargo though)

We can make a new C# project using `dotnet new` and we can build without running using `dotnet build` (This transpiles to CIL not compiles to a binary).

Additionally we can test C# code using `dotnet test`
 

## Basic Calls

`Console`: A built in class for working within the Console window (ie input and output to the console (aka terminal emulator/ shell))

>[!Writing to the Terminal]
> `.WriteLine();` is a method that write text and then makes a new line.
> > Data goes in the parenthesis; the data within the paranthesis will be written to the terminal emulator/ shell. Ie ("Hello, World!"); will print `Hello, World!` to the Console.
>`.Write();`; is  method that writes text and leaves the cursor without making a new line.

>[!Formatting]
> C# provides many specifiers for formatting e.g C for currency
> `Console.Write($"Price: {price:C}")`
> Will print `price` in the format of a currency  
> > (A number may be added to specify how many digits there are after the decimal point)

>[!Composite Strings]
>Composite Strings allow you to inject values of variables into a string (without string interpolation) Example:
>`Console.Write("{0}'s Balance is {1:C2}", userName, userBal)`
>The value of the index ( {0}, {1} etc) corresponds with which variable with be composed into the string
>The above will print
>`USERSNAME's Balance is £X.XX`

Like in most languages instructions are ended with a ;

Comments in C# are noted with //, all comments are ignored.
`// This will be ignored`
`this wont be ignored // this will`

{} Define code blocks (if, for, while etc statments)

## Variables

Variables a named storage location for a piece of data.

#### Declaration:

Decleration is how we make a variable, we must specify the type of data in C# and we cannot change it later.

> `int` is for integers (whole numbers)
> `string` is for text (multiple charachters)

#### Assignment:

Assignment allows us to give data to the variable, using `=` sign.

#### Example:

The above 2 steps can be done in one line like such; `int varname = 12` creates an integer with value 12 named varname.

> [!NOTE]
> Variables are Case Sensitive. Don't use Pascal case- Classes use Pascal case.
>
>  You cannot use any non alphanumeric symbols (besides under scores). 

## Data Type Conversion

> [!Convert Class]
>C# Provides the `Convert` Class, You can use its methods e.g `.ToInt32();` which will convert the inputted data into type 32 bit Integer.

>[!Parsing]
>`int newData = int.Parse(data);` will attempt to turn the data inside the Parse function into an int

>[!Implicit]
>Implicit Conversion can only happen when no data can be lost. Ie converting an `int` to a `long` or converting a `char` to a `string`. Implicit conversion is as the name implies; complit; e.g
>```
>int mew = 32;
>long meow = mew;
>```
> as no data is lost (longs contain all the same and more data than ints), you can convert the int to a long. You cannot implicit conversions of long --> int without using `int.Parse` or `Convert.ToInt32` (both being explicit) Or casting `(int)` 

>[!Casting]
>Casting is very simple:
>```
>
>long meow = 32;
>
>int mew = (int) meow;
>```
>
>This does run the risk of running some data. 
>>[!NOTE]
>>Casting can only be performed between comparable types; e.g `int` and `long` or `char` and `string` NOT `int` and `char`
