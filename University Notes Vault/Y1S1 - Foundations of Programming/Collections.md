>[!Note]
>An "Item" can be any variable
>You cannot mix and match variable types in collections (in C#)

# Array

An Array stores a fixed number of "items"

```cs
int[] arrayName = new int[size]; 
// size is a variable which defines the *Fixed* size of the array of integers
```

>[!Adding Values to Arrays]
>To add a value to an array we specify which "index" aka "slot" in the array the variable will be assigned too.
>```cs
>arrayName[0] = 14; // int value 14 is placed into the first "slot" (index) of the array
>arrayName[1] = 13; // int value 13 is placed into the second index of the array.
>```

>[!Using Values stored in arrays]
>We do it in a very similar way to adding values, just the other way round.
>
>```cs
>int value = arrayName[0]; // the value 14 stored in the first position of arrayName is assigned to the value "value"
>
>Console.WriteLine(arrayName[1]); // Will print the value 13 stored in the second index of the array
>```

Since index's are just numbers, we can iterate over the index of an array using a for loop!

```cs
for (int index = 0; index < arrayName.length; index++) {
	Console.WriteLine(arrayName[index]);
	// Will print 14 and then 13
}
```

Additionally, C# has a special type of for loop, called forEach, mentioned in the [[Iteration]] note; with forEach we can iterate over each item without using the index

```cs
foreach (int value in arrayName) {
	Console.WriteLine(value);
	// This will print 13 and then 14.
}
```

This allows you to modify the values inside the array during your loop, without actually affecting their value in the array.

>[!Choose the simplest loop]
>Use foreach for reading every item. Use for when you need an index or need to replace elements in an array.

# List

List's can store a variable number of "items".

Lists are not present in C# by default, you need to import them; 
```cs
using System.Collections.Generic; 
```

to declare a list use List\<Type> (List\<T>)
```cs
List<string> listName = new List<string> {"meow", "mrrp", "this", "is", "a", "list", "of", "strings"};
```

we can modify the list using a few methods;

```cs
listName.Insert(1, "gay"); // This will shift all values after the 2nd position of the list aka "mrrp" and after, to insert the string "gay".

listName.Remove("meow"); // This will remove all matching strings (and return true if it finds any, false otherwise)

listName.removeAt(1); // This will remove the value at position 2.

bool meowing = listName.Contains("mrrp"); // Will return true if the list contains "mrrp" false otherwise

listName.Sort(); // Will sort the list

listName.Reverse(); // Will revrse the list

listName.add("yay!"); // Will add the input to the end of the list

listName.Count(); // Returns the length of the list
```

>[!Note]
>Use an array when the size of your collection is known, use a List when the size is unkown / could change.

# Dictionary

A dictionary has a named key which identifies each "item" (called "key-value" pairs).

>[!Note]
>Use a dictionary when a "meaningful" (linguistic) key is better than a numeric value for looking up the data. (e.g product name to product price.)

```cs
Dictionary<string, decimal> menu = new Dictionary<string, decimal> {
	["Tea"] = 1.50m,
	["Coffee"] = 2.40m
	["Cake"] = 3.20m
	// The key is stored in brackets, the value is stored in the asignment.	

} // The first type is the type of the key, the second type if the type of the stored items

if(menu.TryGetValue("Coffee", our decimal price)) {
// If the value "Coffee exists in the dictionary, assign its value to the new decimal variable "price"
	Console.WriteLine($"Coffee costs {price:C2}");
	// This will print £2.40
}
```

# Stack / Queue

The order of removal follows a rule; 
	Stack: Last in First Out
	Queue: First in First Out
Stacks;
```cs
Stack<string> history = new Stack<string>();
// creates a stack of strings called history

history.push("how to build a catgirl");
string lastSearch = history.Pop();
// Removed the last value(most recent) from the stack and assigns it to the value lastSearch
```
Queue's;
```cs
Queue<string> printJobs = new Queue<string>();
printJobs.enque("reports.pdf");
string nextJob = printJobs.enque;
// it will remove the first value (the oldest) from the queue and assign it to the valeu nextJob
```

