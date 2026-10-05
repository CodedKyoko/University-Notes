`Console.ReadLine();` Reads a string of text it must be converted to the data type you wish to use it for via explicit casting.

>[!Example]
>```
>Console.WriteLine("How old are You?: ")
>int userAge = Convert.ToInt32(Console.ReadLine());
>
>Console.WriteLine($"You are: {userAge}");
>```
>
>Prints:
>```
>How old are You?: 
><userinp>
>You are: <userinp>
>```



