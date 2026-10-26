# If Statements

```cs
if (boolean == True) {
  // Code that will only execute if the variable "boolean" is true
}
```

The condition inside the ( ) is evaluated, if that evaluates as "True" the code inside the { } will run. If the condition evaluates as false, the code inside the { } will not run

>[!Note]
>You can use &&, ||, ! etc inside an if statement evaluation.
>You may also use == >= =< > < etc

## Else Statement

The Else statement is used to say when if is False; run this instead

```cs
if (somethingthatisFalse) {
	// Code that will not run
} else {
	// Code that will be run
}
```

>[!Note]
>Code inside an else statement will only be run *if* the if statement is false

## Else If Statement

Else If Allows you to add an if statement evaluation to your else case;

```cs
if (somethingthatisFalse) {
	// code that will not run
} else if (boolean == True) {
	// code that will run if boolean is true
}
```

>[!Note]
>If both if statements are false both statements will run. 
>if the first "if" is true, the else if *will not* be evaluated

### Nesting

You can nest multiple if statements

```cs
if (boolean == True) {
	if (boolean2 == True) {
		// Code that will run if if boolean and boolean2 are True
	}
}
```

>[!Note]
>It is recommended to keep nesting shallow where possible, the above example would be better suited to using && instead of nesting.

# Ternary Operator

The ternary operator allows you to assign different values to a variable based on the output of an if-like statement

```cs
int value = -6

int absValue = value >= 0 ? value : -value

// absValue will always be positive
```

In this case, if value is less than 0, its negative value is assigned to to absValue (which makes a positive number), if its more than 0, it will assign itselfa to absValue (so its a positive number)

# Switch

```cs
switch (choice) {
	case 1:
		// Code that executes if choice == 1
		break;
	case 2:
		// Code that executes if choice == 2
		break;
	default:
		// Code that executes if choice == any value that is not a case.
		break;
}
```

Switch statements should be used when you have more than 3 or so if statements.

>[!Note]
>Multiple cases can have one action; for example
>```cs
>switch (choice) {
>	case 1:
>	case 2:
>		// Code that will execute if choice == 1 OR 2  
>		break;		
>     default:
>		// You know what it does
>		break;
>}
>```

## Switch Expression

```cs
int dayNumber = 6;  
string dayName = dayNumber switch  
{  
1 => "Monday",  
2 => "Tuesday",  
3 => "Wednesday",  
4 => "Thursday",  
5 => "Friday",  
6 => "Saturday",  
7 => "Sunday",  
_ => "Invalid day"  
};
```
Functionally it does the exact same thing as the Switch statement syntax, _ is equivalent to the default; case. Used for assigning variables based on a condition (sort of like the Ternary Operator).