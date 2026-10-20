
>[!What is an Expression]
> An expression is a combination of values, variables and operators that the language evaluates to produce a result.
>
>>[!Example]
>>5 + 3 = 8
>>5 - 3 = 2

>[!Concatination]
>It is possible to "add" 2 strings, this is called Concatination
>>[!Example]
>>"5"+"3"="53"
>
>>[!Note]
>>If you attempt to add a string and a number, it will convert the numbers to strings.
## Basic Operators

| Operator | Meaning            |
| -------- | ------------------ |
| +        | Addition           |
| -        | Subtraction        |
| *        | Multiplication     |
| /        | Division           |
| %        | Remainder (modulo) |
>[!Note]
>Division depends on Data Type
>Dividing only int's will result in rounding down to return an int
>
>Dividing (that includes) doubles, will return a double, dividing (that includes) floats will return a float, etc.

You can assign the result of an expression to a variable.

>[!Example]
>```cs
>int num1 = 5;
>int num2 = 3;
>int res = num1 + num2;
>```
>

>[!Compound Assignment]
>You can assign a variable itself operator a value
>>[!Example]
>>`res += 1`
>
>Increases the value of res by one.

>[!Increment and Decrement]
>You can increase and decrease variables by one
>>[!Example]
>>```cs
>>int res = 5;
>>res ++; // res is now 6
>>int res2 = 5;
>>res2 --; // res is now 4
>>```
>
>>[!Note]
>>The side you place the increment/decrement effects which order instructions occur.
>> If you place it before your variable, it will execute the Change of the variable, before parsing the variable to the method/ before executing the code.
>> If you place it after the variable it will execute after the method/ line of code
>> >[!Example]
>> >```cs
>> >int number = 5;
>> >Console.WriteLine(number++); // Prints 5, and then is incremented to 6
>> >Console.WriteLine(++number); // Is incremented to 7, and then prints 7.
>> >```


>[!Modulus]
>Modulus returns the remainder of a division
>a % b


### Order of Operations

Parentheses -> ++ / -- -> * / / -> + / - -> Assignment

When shared, evaluates left 

## Comparison Operators

| Operator | Meaning                            |
| -------- | ---------------------------------- |
| ==       | Check if Equal                     |
| !=       | Check if NOT Equal                 |
| >        | Check if Greater than              |
| <        | Check if Less than                 |
| >=       | Check if Greater than or equal too |
| <=       | Check if Less than or equal too    |
>[!Note]
>== cares about Type, `double == int` would return false even if the logical value is the same

## Logical Operators

| &&   | Logical AND |
| ---- | ----------- |
| \|\| | Logical OR  |
| !    | Logical NOT |
# Simplified Solution to vending machine;

```cs
Console.WriteLine("How much does the product Cost?: ");
decimal price = Convert.ToDecimal(Console.ReadLine());
Console.WriteLine(("How much was paid?: "));
decimal paid = Convert.ToDecimal(Console.ReadLine());

if (paid >= price){
  decimal change = Math.Abs(price - paid);

  Console.WriteLine($"Change to issue: {change:C2}");

  decimal pound2 = Math.Floor(change/2); 
  change -= pound2*2;
  decimal pound1 = Math.Floor(change/1);
  change -=pound1*1;
  decimal pence50 = Math.Floor(change/0.5m);
  change -=pence50*0.5m;
  decimal pence20 = Math.Floor(change/0.2m);
  change -=pence20*0.2m;
  decimal pence10 = Math.Floor(change/0.1m);
  change -=pence10*0.1m;
  decimal pence5 = Math.Floor(change/0.05m);
  change -=pence5*0.05m;
  decimal pence2 = Math.Floor(change/0.02m);
  change -=pence2*0.02m;
  decimal pence1 = Math.Floor(change/0.01m);
  change -=pence1*0.01m;

  Console.WriteLine($"Change Issued: {pound2}: 2 Pound Coins, {pound1}: 1 Pound Coins, {pence50}: 50 Pence Coins, {pence20}: 20 Pence Coins, {pence10}: 10 Pence Coins, {pence5}: 5 Pence Coins, {pence2}: 2 Pence Coins, {pence1}: 1 Pence Coins");
}
else {
  Console.WriteLine($"Payment of {paid:C2} is not suffecient to purchase item of value {price:C2}");
}
```

No but like actually his is way fucking over complicated i stg.