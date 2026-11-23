Access modifiers control where a type or member can be accessed.

>[!Example] Public
>Accessible from other code that can access the containing type 

>[!Example] Private
>Accessible only within the containing type
>Members of a class are Private by default.
>>[!Note]
>>A class can expose operations without exposing the data itself (ie using a getter and setter for private data)
>
>>[!Example]
>>```cs
>>public class Student  {  
>>	
>>	public string Name = "";  
>>	private int score;  
>>	
>>	public bool SetScore(int newScore)  {  
>>		if (newScore < 0 || newScore > 100)  {return false; }  
>>		score = newScore;  
>>		return true;  
>>	}
>>	  
>>	public int GetScore() { return score; }  
>>}
>>```
>The value of `Score` is not directly accesible outside the `Class` (as its `private`). Meaning it cannot be directly assigned and referenced, however the getter and setter methods `SetScore` and `GetScore` are inside the `Class`, so they can reference and manipulate the variable `Score`. And as they are `public` they are accesible outside the `Class`.
>>
>>This is called **Encapsulation**
>
>>[!Properties]
>>```cs
>>public class Student  {  
>>	public string Name = "";  
>>	private int score;  
>>	
>>	public int Score  {  
>>		get { return score; }  
>>		set  {  
>>			if (value >= 0 && value <= 100)  { score = value; }  
>>		}  
>>	}  
>>}
>>```
>>This is an example of a **Property** Properties appear like regular field to the caller, but it maintains the advantages of encapsulation (e.g. being able to reject invalid inputs, and manipulate inputs)


