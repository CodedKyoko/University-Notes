# Stopwatch

The stopwatch from System.Diagnostics measures elapsed time.

```cs
using System.Diagnostics;

Stopwatch stopwatch = Stopwatch.StartNew();

// Creates a Stopwatch called "stopwatch" and starts it.

// Code to measure execution time off.

stopwatch.Stop();
Console.WriteLine($"Elapsed: {stopwatch.ElapsedMilliseconds} ms)
// stops the Stopwatch called "stopwatch" and prints the time it recorded in milliseconds.
```

>[!Note]
>This is useful for observing the time taken to process a collection, BUT it does not prove that one small test is *always* faster than enough.

# Thread.Sleep

Thread.Sleep pauses the current program (thread) for a specified number of milliseconds.

```cs
using System.Threading;

Console.WriteLine("Ready...");
Thread.Sleep(1000);
Console.WriteLine("Set...");
Thread.Sleep(1000);
Console.WriteLine("Go!");
// there will be a 1 second pause between each print
```

>[!Note]
>Sleeping makes a demonstration easier to follow but it deliberately makes the program wait, Do not use it as a way to co-ordinate real background work.

