# Loops

Loops allow us to repeat the same code action multiple times (either changing the functionality based on the number of iterations, or the exact same every time, without having to copy and paste the same line 100's of times).

## For Loops

For loops use an iterator (a number that has some operation (typically increment by 1) occur to it every time the for loop runs) to keep track of the iteration

```cs
for (int numbner = 1; number >= 5, number++) {
	// Code that will run 5 times
}
```

as you can see, a for loop is in 3 parts, part 1, introduces the iterator (it can be a new variable, or a pre-existing one); part 2, sets the condition for ending the for loop; part 3 tells the iterator what do after each iteration.

## Foreach Loops

Foreach loops can be used to run a block of code on / per each item in a list/ char in a string

```cs
string message = "Hi!";  
foreach (char character in message)  
{  
	Console.WriteLine(character); // Print each charachter in the string "Hi!" on a new line
}
```

output:
```
H
i
!
```

## While Loops

While loops execute based on a boolean.

While x is True: do this.

If the conditional is false initially While will not run its code block. `while (True)` would run forever.

```cs
while (isFixed == False) {

// Some code to run, and to decide if isFixed should be true, the while statement will run until isFixed = True.

}
```

## Do ... While

(Aka Do ... Untill)

Do Until is the same as while, but it must at least run once.

```cs
do {

	// This will be executed exactly once

} while (somethingFalse)
```

>[!Note]
>`break;` can be used to escape the current loop no matter the value of the while condition or the for iterator.
>`continue;` allows you to skip the current iteration of the loop, and then continue running the loop

# You can Nest loops. 

