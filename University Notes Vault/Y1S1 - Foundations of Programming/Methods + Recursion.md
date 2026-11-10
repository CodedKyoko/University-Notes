## Methods

A method is a way to make a re-usable block of code. For example if we need to greet multiple students at arbitrary points in your code.

```cs
static void Greet(string name) {
	Console.WriteLine($"Welcome, {name}!");
}

Greet("Alice");
Greet("Bob");
Greet("Sam");
```

### Anatomy of a Method

`static`: here the local function cannot use variables from the surrounding code directly
`void`: tells you that nothing will be returned by this method, other values like `int`, `decimal`, `string` etc can be used to set up a return value.

Paramaters are placed between the ( ) you maye have as many as you need. Define their type and then name them, when you call the function you need to pass in the same *number* and *types* of arguments!

The body of the method (everything within {}) is executed when the method is called, to return values back to the place it was called use the `return` command.

>[!Example]
>```cs
>static int Add(int first, int second) {
>	int total = first + second;
>	return total;
}
>
>int result = Add(6,7);
>Console.WriteLine(result);
>```
>

>[!Note]
>Calling `return;` *always* ends the method.
>> Methods that return values are typically called Functions.

### Scope

Variables defined within a method (that are not returned) are local to the method. Including any Parameters passed into the Method. No code outside of the method can use those variables.

Each "invocation" (Usage) of the method has its own set of these variables, which will not interact with each other.

### Pass by Value

The method receives a copy of the arguments value. Assigning a new value to the parameter does not change the caller's variable

### Pass by Reference

The Method receives a reference to the caller's argument itself, so the method can change that value.

>[!Note]
>In C# arguments are passed by value *by default* use `ref` or `out` to pass a variable by reference; `in` provides read-only access to the reference.
> For any Array passing by value copies its reference, not the array. The method can still change elements in the shared array.

>[!Example]
>```cs
>static void Increase(ref int number) {
>	number++;
>}
>int score - 10;
>Increase(ref score);
>Console.WriteLine(score); // Prints 11.
>```

>[!Example]
>An out value creates a variable as an additional return
>```cs
>string input = "42";
>bool valid = int.TryParse(input, out number);
>
>if (valid) {
>	Console.WriteLine(number * 2); 
>}
>```

## Recursion

A Recursive Method is a method that calls itself. Recursion is useful when a problem contains smaller versions of itself. E.g. Factorials.

**The Base Case**: The final step; gives an answer without calling anymore instances of itself

**Recursive Step**: A step deeper into the recursive memory hell hole, gradually approaching the base case.

>[!Note]
>Iteration (loops) is almost always more effective than Recursion (ESPECIALLY regarding memory usage).

>[!Example]
>```cs
>static void Countdown(int number) {
>	if (number <= 0) {
>		Console.WriteLine("Go!);
>		return;
>	}
>	Console.WriteLine(number);
>	Countdown(number-1);
>}
>Countdown(3);
>```
>Honestly a horrible usecase... just use a for loop.

### The call stack.

- A call pauses its caller while the called method runs.
- Each active invocation (call/ usage) has its own parameters, local variables and return position.
- When a call returns, execution returns in the caller.
- Recursive calls follow the exact same rules as any method calls.

>[!Warning]
>Missing the base case, or failing to move towards it, is very bad, and can trap you in a near infinite loop (until you run out of memory).

### Designing Recursive Calls.

- Define the input and what the method should *do* or *return*.
- Identify the smallest case that can be solved directly.
- Express the answer using a smaller instance of the same problem.
- Check that every recursive call moves towards the base case
- Trace a small example and test the base case and invalid inputs.

