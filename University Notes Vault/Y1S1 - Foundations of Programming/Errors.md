There are 3 types of errors a program can encounter while its running.

# Compile-time

When the compiler rejects the program; for example a missing semicolon, type mismatch or out of scope variable.

>[!Note]
>Not every compile time error is a syntax error, for example a Type mismatch is a compile time error, but its syntax is valid.

>[!Example] 
> ```cs
> int score = "high"; // type mismatch
> Console.WriteLine(score) // Mising ; (Semicolon)
> ```

# Runtime

The program starts but an operation fails: For example invalid input or an array index outside its bounds.

>[!Example]
>```cs
>Console.Write("Enter a whole number: ");
>int number = int.Parse(Console.ReadLine()!);
>Console.Writeline(100 / number);
>```
>Text such as "hello" causes a FormatException
>A zero input causes a DivideByZeroException for integer division.
>An unhandled Exception normally terminates the program and produces a stack trace.
>The ! suppresses a compiler warning; it does not prevent a null value at run time.

## Handling Exceptions

An operation can "throw" an exception, a handler can "catch" it. 
The call stack helps the locate the operation and the sequence of calls that reached it.
Catch an exception only when you can respond appropriately such as reporting a problem or recovering it.

>[!Note]
>Not every exception is a bug; A missing file or unavailable connection may be a condition the program has to handle.

### Try-Catch-Finally

```cs
try {

	// Code that may throw an exception

} catch(TypeOfException) {

	// Respond to this kind of Exception

} finally {

	// Cleanup, whether or not the exception occurred.

}
```

>[!Note]
>the Finally block is optional, and is usually run after the try or catch block even if no exception occurred.

>[!Note]
>You may have more than one catch block, each one handles an individual Exception

>[!Example]
>```cs
>try {
>	int number = int.Parse(Console.ReadLine);
>	Console.WriteLine(100/number)
>} catch(FormatException) {
>	Console.WriteLine("Enter a Whole Number");
>} catch(DivideByZeroException) {
>	Console.WriteLine("The number must not be Zero);
>}
>```

>[!Note]
>Exception error can be used to catch any Exception. <- More general Exceptions like Exception error should be used afer more spesific Exceptions like FormatException

## Validate User Input

TryParse returns false when it fails and true when it succeeds, use if and else blocks to validate that the Parse succeeded.



# Logic

The program runs but produces an incorrect result: for example, using the wrong formula.

>[!Example]
>```cs
>int first = 60;
>int second = 80;
>double average = first + second / 2.0; // Order of operations is wrong (logic error).
>Console.WriteLine(average);
>```
