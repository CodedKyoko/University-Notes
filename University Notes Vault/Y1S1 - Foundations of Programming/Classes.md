A class defines a "group" of variables (qualities) and methods / functions (behaviours).

A particular example of that group can then be represented as an object.

# Classes

```cs

public class Student {

	public string name = "";
	public int score;
	
	public void Introduce() {
	
		Console.WriteLine($"{name} scored {score}");
	}
}

```

A class can be treated as a data type, and used to declare new variables called Objects

>[!Note]
> When using top level statements code has to come *before* class definitions.

# Objects

As mentioned above Objects are a singular instance of an object

```cs

Student alice = new Student();

alice.name = "Alice";
alice.score = 85;

Console.WriteLine($"{alice.name} scored {alice.score}"); 

// Or use the method in the class

alice.Introduce();

```

Infinite objects can be created from a single class; they all have their own unique instance of the data and methods associated with that class.

>[!Note]
> Static methods belong to a type; call it using the types name (class name)
> Instance methods belong to an object; call it using the objects name
> 
> Static methods have no implicit object associated with them
> Static methods can access static state; they are not necessarily stateless.
>
>>[!Example]
>>
>>```cs
>>public class Student {
>>
>>	public static int PassMark = 50; // All objects made form this clas will have the the same value for the variable PassMark
>>	public string Name = "";
>>	public int Score;
>>
>>	public static bool IsPassing(int score) {
>>		return score >= PassMark; // This function cannot acces the non static elements of the Object (without them being passed as parameters) but it cann acces the static values all objects have.
>>	}
>>	public void ShowResult() {
>>		Console.WriteLine($"{Name} scored {Score}");
>>	}
>>}
>>```

