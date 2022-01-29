# C#
C# documentation

## Basics

>So in this section, you learned the basics of C#.
>
>C# vs .NET
>
>C# is a programming language, while .NET is a framework. It consists of a run-time environment (CLR) and a class library that we use for building applications.
>
>CLR
>
>When you compile an application, C# compiler compiles your code to IL (Intermediate Language) code. IL code is platform agnostics, which makes it possible to a take a C# program on a different computer with different hardware architecture and operating system and run it. For this to happen, we need CLR. When you run a C# application, CLR compiles the IL code into the native machine code for the computer on which it is running. This process is called Just-in-time Compilation (JIT).
>
>Architecture of .NET Applications
>
>In terms of architecture, an application written with C# consists of building blocks called classes. A class is a container for data (attributes) and methods (functions). Attributes represent the state of the application. Methods include code. They have logic. That's where we implement our algorithms and write code.
>
>A namespace is a container for related classes. So as your application grows in size, you may want to group the related classes into various namespaces for better maintainability.
>
>As the number of classes and namespaces even grow further, you may want to physically separate related namespaces into separate assemblies. An assembly is a file (DLL or EXE) that contains one or more namespaces and classes. An EXE file represents a program that can be executed. A DLL is a file that includes code that can be re-used across different programs.
>
>In the next section, you'll learn about basics of the C# language, including variables, constants, type conversion and operators.

# <br>Primitive Types and Expressions
## Variable types , formate string and constant in code
```
using System;
namespace ConsoleApp2
{
    class Program
    {
        static void Main(string[] args)
        {
            /* byte number = 2;
            int count = 10;
            float totalPrice = 20.95f;
            char character = 'A';
            string firstName = "Mosh";
            bool isWorking = true; */

            //You can also declare variables with var
            /*var number = 2;
            var count = 10;
            var totalPrice = 20.95f;
            var character = 'A';
            var firstName = "Mosh";
            var isWorking = true;

            Console.WriteLine(number);
            Console.WriteLine(count);
            Console.WriteLine(totalPrice);
            Console.WriteLine(character);
            Console.WriteLine(firstName);
            Console.WriteLine(isWorking);*/

            // fromate strings
            /*Console.WriteLine("{0} {1}", byte.MinValue, byte.MaxValue); ;
            Console.WriteLine("{0} {1}", float.MinValue, float.MaxValue);*/

            // constant
            const float PI = 3.14f;
            // PI = 1; // you can not change the value of const variable it will give error
        }
    }
}
```

## Type conversion theory

>In C#, there are two types of casting:
>
>Implicit Casting (automatically) - converting a smaller type to a larger type size<br>
>char -> int -> long -> float -> double <br>
>Explicit Casting (manually) - converting a larger type to a smaller size type<br>
>double -> float -> long -> int -> char <br>
>
>### Implicit Casting<br>
>Implicit casting is done automatically when passing a smaller size type to a larger size type:
```
int myInt = 9;
double myDouble = myInt;       // Automatic casting: int to double

Console.WriteLine(myInt);      // Outputs 9
Console.WriteLine(myDouble);   // Outputs 9
```

>### Explicit Casting<br>
>Explicit casting must be done manually by placing the type in parentheses in front of the value:
```
double myDouble = 9.78;
int myInt = (int) myDouble;    // Manual casting: double to int

Console.WriteLine(myDouble);   // Outputs 9.78
Console.WriteLine(myInt);      // Outputs 9
```
>### Type conversion in code
```
using System;

namespace type_conversion
{
    class Program
    {
        static void Main(string[] args)
        {
            // Implicit Casting 
            byte b = 1;
            int i = b;
            Console.WriteLine(i);

            // Explicit Casting
            int a = 10;
            byte j = (byte)a;
            Console.WriteLine(j);

            // Non-compatible
            // converting string to number with 'Convert' class function
            var number = "1234";
            int k = Convert.ToInt32(number);
            Console.WriteLine(k);

            // converting string into boolean
            string str = "true";
            bool l = Convert.ToBoolean(str);
            Console.WriteLine(l);
        }
    }
}
```
## Operators
>- Arithmetic Operators
>- Comparison Operators
>- Assigment Operators
>- Logical Operators
>- Bitwise Operators

>### Arithmetic Operators
>Arithmetic operators are used to perform common mathematical operations:
>![2022-01-02](https://user-images.githubusercontent.com/92302123/147879525-0c8cfd9f-5423-4b4c-b352-f012c23c39f6.png)
>### Comparison Operators
>Comparison operators are used to compare two values:
>![2022-01-02 (1)](https://user-images.githubusercontent.com/92302123/147880091-1be55e51-a77a-4f48-8324-4b68c1525f71.png)
>### Assignment Operators
>Assignment operators are used to assign values to variables.
>![2022-01-02 (2)](https://user-images.githubusercontent.com/92302123/147880270-fdb86303-3dbc-41bf-8363-a7c0e73a6bd5.png)
>### Logical Operators
>Logical operators are used to determine the logic between variables or values:
>![2022-01-02 (3)](https://user-images.githubusercontent.com/92302123/147880356-0de8afde-a4cb-4cc0-a634-a4fbfe2ebda2.png)
>### Bitwise Operators
>![2022-01-02 (4)](https://user-images.githubusercontent.com/92302123/147880497-3d028dd1-0d57-4469-9840-19ec976274e3.png)
## Primitive Types and Expressions (full summery)
>[13.1 Summary Primitive Types And Expressions.pdf](https://github.com/Bhavesh-0609/c-sharp/files/7800777/13.1.Summary.Primitive.Types.And.Expressions.pdf)

# Non-Primitive Types
## Class
>A class is a user-defined blueprint or prototype from which objects are created. Basically, a class combines the fields and methods(member function which defines actions) into a single unit. In C#, classes support polymorphism, inheritance and also provide the concept of derived classes and base classes.
```
using System;

namespace classes
{
    public class Person
    { 
        public string FirstName;
        public string LastName;

        public void Introduce()
        {
            Console.WriteLine("My name is " + FirstName + " " + LastName);
        }
    }
    class Program
    {
        static void Main(string[] args)
        {
            Person john = new Person();
            // var john = new Person(); // u can also write like this
            john.FirstName = "John";
            john.LastName = "Smith";
            john.Introduce();
        }
    }
}

```
## Array
>Array is a data structure to store a collection of variables of same type

>syntax
```
int[] numbers = new int[3];
// int[] number = new int[3] {1, 2, 3}; // declaring and assigning value at same time
```
>### Code of array
```
using System;

namespace array_in_c_sharp
{
    class Program
    {
        static void Main(string[] args)
        {
            int[] numbers = new int[3];
            // var number = new int[3]; // you can also write like this
            numbers[0] = 1;

            Console.WriteLine(numbers[0]);
            Console.WriteLine(numbers[1]); // empty arrays default value in int is 0
            Console.WriteLine(numbers[2]);

            var flags = new bool[3];
            flags[0] = true;

            Console.WriteLine(flags[0]);
            Console.WriteLine(flags[1]); // empty arrays default value in boolean is false
            Console.WriteLine(flags[2]);

            var names = new string[3] { "Jack", "John", "Mary" }; //object initialization syntax
        }
    }
}
```
## Strings
>String is a sequence of characters.
>e.g. "Hello World"

>Syntax
```
string firstName = "Mosh";
```
>Concatenating strings
```
string name = firstName + " " + lastName;
```
>String formating
```
string name = string.Format ("{0} {1}", firstName, lastName);
```
>Using string join
```
var numbers = new int[3] {1,2,3};
string list = string.Join(",", numbers);
```
>String Elements
```
string name = "Mosh";
char fristChar = name[0]; // output will be 'M' from "Mosh"
// name[0] = 'm'; // this will give error b'cause Strings are immutable - Once you create them, you cannot change them.
```
>### Important in strings
>
>Strings are immutable - Once you create them, you cannot change them. like showen below
```
// name[0] = 'm'; // this will give error b'cause Strings are immutable - Once you create them, you cannot change them.
```
### Escape characters
![2022-01-03 (1)](https://user-images.githubusercontent.com/92302123/147927980-ac6129df-8c18-40ce-b12f-846b05e680f0.png)
>### Verbatim string
>
>adding path is string will not look good because of escape characters because you have to add doble back slash for a single back slash
>
>e.g.
```
string path = "c:\\projects\\project1\\folder1"; // dont do this
```
>in verbatim string you dont have to add double back slash like shown belowe
```
string path = @"c:\projects\project1\folder1"; // it is verbatim string
```
>### Full code of strings
```
using System;

namespace strings
{
    class Program
    {
        static void Main(string[] args)
        {
            string firstName = "Mosh";
            string lastName = "Hamedani";

            var fullName = firstName + " " + lastName;

            var myFullName = string.Format("My name is {0} {1}", firstName, lastName); // concatinating string with function

            var names = new string[3] { "John", "Jack", "Marry" }; // string array
            var formattedName = string.Join(",", names); // formating strings with couma "," 
            // Console.WriteLine(formattedName);

            var text = "Hi John\nLook into the following paths\nc:\\folder\\folder2\nc:\\folder3\\folder4"; // this is simple string and not look so good
            var verbString = @"Hi John
                Look into the following paths
                c:\folder\folder2
                c:\folder3\folder4"; // this is verbatim string and its denoted with @ sign in verbatim string you dont have to use escape characters
            Console.WriteLine(text);
        }
    }
}
```

## Enum
>An enum is a special "class" that represents a group of constants (unchangeable/read-only variables).
>In enum if we don't set any value to the members of enum then the first member is going to be automatically set to zero and from there every member's value will be increamented by 1.
>syntax
```
public enum ShippingMethod
{
    RegularAirMail = 1,
    RegisteredAirMail = 2,
    Express = 3
}
```
>How to access enum
```
var method = ShippingMethod.Express;
```
>Enum's basic data type is int. if you want to change to other data type then you have to declere enum like this
```
public enum ShippingMethod : byte
{
    RegularAirMail = 1,
    RegisteredAirMail = 2,
    Express = 3
}
```
> ### Enum full code
```
using System;

namespace enum_in_c_sharp
{
    public enum ShippingMethod
    {
        RegularAirMail = 1,
        RegisteredAirMail = 2,
        Express = 3
    }
    class Program
    {
        static void Main(string[] args)
        {
            var method = ShippingMethod.Express;
            Console.WriteLine((int)method); // converting string to their number(int)

            var methodId = 3;
            Console.WriteLine((ShippingMethod)methodId); // converting the number to their string

            Console.WriteLine(method.ToString());

            var methodName = "Express";
            var shippMethod = (ShippingMethod)Enum.Parse(typeof(ShippingMethod), methodName);
            Console.WriteLine(shippMethod);
        }
    }
}
```
## Value type and Reference type
>### Value type 
>A data type is a value type if it holds a data value within its own memory space. It means the variables of these data types directly contain values.
> 
>The following data types are all of value type:
>- bool
>- byte
>- char
>- decimal
>- double
>- enum
>- float
>- int
>- long
>- sbyte
>- short
>- struct
>- uint
>- ulong
>- ushort
>
>#### Passing Value Type Variables
>When you pass a value-type variable from one method to another, the system creates a separate copy of a variable in another method. If value got changed in the one method, it wouldn't affect the variable in another method.
>
>Example: Passing Value Type Variables
```
static void ChangeValue(int x)
{
    x =  200;

    Console.WriteLine(x);
}

static void Main(string[] args)
{
    int i = 100;

    Console.WriteLine(i);
    
    ChangeValue(i);
    
    Console.WriteLine(i);
}
```
>### Reference Type
>Unlike value types, a reference type doesn't store its value directly. Instead, it stores the address where the value is being stored. In other words, a reference type contains a pointer to another memory location that holds the data.
>
>The followings are reference type data types:
>- String
>- Arrays (even if their elements are value types)
>- Class
>- Delegate
>
>#### Passing Reference Type Variables
>When you pass a reference type variable from one method to another, it doesn't create a new copy; instead, it passes the variable's address. So, If we change the value of a variable in a method, it will also be reflected in the calling method.
>
>Example: Passing Reference Type Variable
```
static void ChangeReferenceType(Student std2)
{
    std2.StudentName = "Steve";
}

static void Main(string[] args)
{
    Student std1 = new Student();
    std1.StudentName = "Bill";
    
    ChangeReferenceType(std1);

    Console.WriteLine(std1.StudentName);
}
```
> ### Value type and Reference type full code
```
using System;

namespace reference_type_and_value_type
{
    class Program
    {
        static void Main(string[] args)
        {
            var a = 10;
            var b = a;
            b++;
            Console.WriteLine(string.Format("a : {0}, b: {1}", a, b));
            
            var array1 = new int[3] { 1, 2, 3 };
            var array2 = array1;
            array2[0] = 0;
            Console.WriteLine(string.Format("array1[0] : {0}, array2[0]: {1}", array1[0], array2[0]));
        }
    }
}
```
> ### Value type and Reference type full code - 2
```
 using System;

namespace Reference_Types_and_Value_Types_2
{
    public class Person
    {
        public int Age;
    }
    class Program
    {
        static void Main(string[] args)
        {
            var number = 1;
            Increment(number);
            Console.WriteLine("number : " + number);

            var person = new Person() { Age = 20 };
            MakeOld(person);
            Console.WriteLine(person.Age); 
        }
        public static void Increment(int number)
        {
            number += 10;
        }
        
        public static void MakeOld(Person person)
        {
            person.Age += 10;
        }
    }
}
```
## Full summary Non Primitive Types
[15.1 Summary Non Primitive Types.pdf](https://github.com/Bhavesh-0609/c-sharp/files/7809452/15.1.Summary.Non.Primitive.Types.pdf)

# Control flow
>In this part of the C# tutorial, will talk about the flow control. We define several keywords that enable us to control the flow of a C# program.
>
>In C# language there are several keywords that are used to alter the flow of the program. When the program is run, the statements are executed from the top of the source file to the bottom. One by one. This flow can be altered by specific keywords. Statements can be executed multiple times. Some statements are called conditional statements. They are executed only if a specific condition is met.

## Conditional statements
>- If/else statement
>- Switch/case statement
>- Conditional operators: a?b : c
>
>### If/else statement
>#### If statement
>The if keyword is used to check if an expression is true. If it is true, a statement is then executed. The statement can be a single statement or a compound statement. A compound statement consists of multiple statements enclosed by the block. A block is code enclosed by curly brackets.
>#### Else statement
>We can use the else keyword to create a simple branch. If the expression inside the square brackets following the if keyword evaluates to false, the statement following the else keyword is automatically executed.
>#### Else if
>We can create multiple branches using the else if keyword. The else if keyword tests for another condition if and only if the previous condition was not met. Note that we can use multiple else if keywords in our tests.
>#### Syntax
```
if (condition)
{
    // code
}
else if (anotherCondition)
{
    // code
}
else
{
    // code
}
```
>### Switch statement
>The switch statement is a selection control flow statement. It allows the value of a variable or expression to control the flow of program execution via a multi-way branch. It creates multiple branches in a simpler way than using the combination of if/else if/else statements.
>
>We have a variable or an expression. The switch keyword is used to test a value from the variable or the expression against a list of values. The list of values is presented with the case keyword. If the values match, the statement following the case is executed. There is an optional default statement. It is executed if no other match is found.
>
>Since C# 7.0, the match expression can be any non-null expression.
>#### Syntax
```
switch(role)
{
    case Role.Admin:
        ...
        break;
    case Role.Moderator:
        ...
        break;
    default:
        ...
        break;
}
```
>### Conditional operator
>C# includes a decision-making operator ?: which is called the conditional operator or ternary operator. It is the short form of the if else conditions.
```
bool isGoldCustomer = true;
float price = (isGoldCustomer) ? 19.95f : 29.95f;
Console.WriteLine(price);
```
>### Full code of Conditional statement
```
using System;

namespace demo_if_else
{
    public enum Season
    {
        Spring,
        Summer,
        Autumn,
        Winter
    }
    class Program
    {
        static void Main(string[] args)
        {
            /*int hour = 16;

            if (hour > 0 && hour < 12)
            {
                Console.WriteLine("It's morning.");
            }
            else if (hour >= 12 && hour < 18)
            {
                Console.WriteLine("It's afternoon.");
            }
            else
            {
                Console.WriteLine("It's evening.");
            }*/

            // Another example

            //bool isGoldCustomer = true;
            /*float price;

            if (isGoldCustomer)
            {
                price = 19.95f;
            }
            else
            {
                price = 29.95f;
            }*/

            // you can also write like this
            /*float price = (isGoldCustomer) ? 19.95f : 29.95f;
            Console.WriteLine(price);*/


            // switch case
            var season = Season.Autumn;
            switch (season)
            {
                case Season.Autumn:
                    Console.WriteLine("It's autumn and a beautiful season.");
                    break;
                case Season.Summer:
                    Console.WriteLine("It's perfect to go to beach.");
                    break;
                default:
                    Console.WriteLine("I don't understand that season!");
                    break;
            }
        }
    }
}
```
## Loops
>Looping in a programming language is a way to execute a statement or a set of statements multiple times depending on the result of the condition to be evaluated to execute statements. The result condition should be true to execute statements within loops.
>
>Loops are mainly divided into two categories:
>
>**Entry Controlled Loops**: The loops in which condition to be tested is present in beginning of loop body are known as Entry Controlled Loops. while loop and for loop are entry controlled loops.
>
>**Exit Controlled Loops**: The loops in which the testing condition is present at the end of loop body are termed as Exit Controlled Loops. do-while is an exit controlled loop.
Note: In Exit Controlled Loops, loop body will be evaluated for at-least one time as the testing condition is present at the end of loop body.
>
>There is four types of loops
>1. For loops
>2. Foreach loops
>3. While loops
>4. Do-while loops
>
>### For loops
>for loops are preferred when the number of times loop statements are to be executed is known beforehand. The loop variable initialization, condition to be tested, and increment/decrement of the loop variable is done in one line in for loop thereby providing a shorter, easy to debug structure of looping.
```
for (var i = 0; i < 10; i++)
{
    // code
}
```
>#### Full code of for loop
```
using System;

namespace for_loop
{
    class Program
    {
        static void Main(string[] args)
        {
            for (var i = 0; i<=10; i++)
            {
                if (i%2 == 0)
                {
                    Console.WriteLine(i);
                }   
            }

            for (var i = 10; i>=0; i--)
            {
                if (i % 2 == 0)
                {
                    Console.WriteLine(i);
                }
            }
        }
    }
}
```
>### Foreach
>The foreach loop is used to iterate over the elements of the collection. The collection may be an array or a list. It executes for each element present in the array.
```
foreach (var number in numbers)
{
    // code
}
```
>#### Full code of foreach loop
```
using System;

namespace foreach_loop
{
    class Program
    {
        static void Main(string[] args)
        {
            var name = "John smith";

            //for (var i = 0; i < name.Length; i++)
            //{
            //    Console.WriteLine(name[i]);
            //}

            foreach (char c in name)
            {
                Console.WriteLine(c);
            }
            
            var numbers = new int[] { 1, 2, 3, 4, 5, 6 };
            foreach(var number in numbers)
            {
                Console.WriteLine(number);
            }
        }
    }
}
```
>### While loop
>The test condition is given in the beginning of the loop and all statements are executed till the given boolean condition satisfies when the condition becomes false, the control will be out from the while loop.
```
while (i < 10)
{
    // code
    i++;
}
```
>### Do-while loop
>do while loop is similar to while loop with the only difference that it checks the condition after executing the statements, i.e it will execute the loop body one time for sure because it checks the condition after executing the statements.
```
do
{
    // code
    i++;
} while (i < 10);
```
## Break and continue
>- Break : jumps out of the loop
>- Countinue : jumps to the next iteration
>#### Full code of while loop and break,countinue
```
using System;

namespace while_loops
{
    class Program
    {
        static void Main(string[] args)
        {
            // var i = 0;
            /*while (i <= 10)
            {
                if (i%2 == 0)
                {
                    Console.WriteLine(i);
                }
                i++;
            }*/

            while (true)
            {
                Console.Write("Type your name : ");
                var input = Console.ReadLine();

                if (!String.IsNullOrWhiteSpace(input))
                {
                    Console.WriteLine("@Echo : " + input);
                    continue;
                }
                break;
            }
        }
    }
}
```
## Random
>Random class in C# is used to get a random integer number. This method can be overloaded by passing different parameters to it as follows: Next() Next(Int32) Next(Int32, Int32)
>#### Full code
```using System;

namespace random_class
{
    class Program
    {
        static void Main(string[] args)
        {
            //var random = new Random();
            //for(var i = 0; i < 10; i++)
            //    Console.WriteLine(random.Next(1,10));

            var random_char = new Random();
            var buffer = new char[10];
            for (var i = 0; i < 10; i++)
            {
                Console.Write((char)random_char.Next(97, 122)); // printing random string with asci value
                buffer[i] = (char)('a' + random_char.Next(0, 26)); // another way to generate string and store it into array
            }
            Console.WriteLine();
            Console.WriteLine(buffer);
        }
    }
}
```
## Controle flow exersices
>1- Write a program to count how many numbers between 1 and 100 are divisible by 3 with no remainder. Display the count on the console.
>
>2- Write a program and continuously ask the user to enter a number or "ok" to exit. Calculate the sum of all the previously entered numbers and display it on the console.
>
>3- Write a program and ask the user to enter a number. Compute the factorial of the number and print it on the console. For example, if the user enters 5, the program should calculate 5 x 4 x 3 x 2 x 1 and display it as 5! = 120.
>
>4- Write a program that picks a random number between 1 and 10. Give the user 4 chances to guess the number. If the user guesses the number, display “You won"; otherwise, display “You lost". (To make sure the program is behaving correctly, you can display the secret number on the console first.)
>
>5- Write a program and ask the user to enter a series of numbers separated by comma. Find the maximum of the numbers and display it on the console. For example, if the user enters “5, 3, 8, 1, 4", the program should display 8.
>
>#### Solution
```
using System;

namespace Controle_flow_exercise
{
    class Program
    {
        static void Main(string[] args)
        {
            // exersice 1
            /*var count = 0;
            for(var i = 1; i < 100; i++)
            {
                if (i % 3 == 0)
                    count++;
            }
            Console.WriteLine("The count of numbers which divided by 3 is " + count);*/

            // exercise - 2
            /*int i = 0,count2=0;
            string[] arr = new string[100];
            Console.WriteLine("Enter \"ok\" to EXIT");
            while(arr[i] != "ok")
            {
                i++;
                arr[i] = Console.ReadLine();
            }
            for(var j = 1; j < i; j++)
            {
                count2 += Convert.ToInt32(arr[j]);
            }
            Console.WriteLine("The sum of numbers is : " + count2);*/

            // exercise - 3
            /*int fact = Convert.ToInt32(Console.ReadLine());
            int count = fact;
            for(int i = 1; i < count; i++)
            {
                fact = fact * i;
            }
            Console.WriteLine(count + "! =" +fact);*/

            // exercise - 4
            /*var random = new Random();
            int randomNumber = random.Next(1, 10), userGuess;
            Console.Write("Guess number between 1 to 10 : ");
            userGuess = Convert.ToInt32(Console.ReadLine());
            if (randomNumber == userGuess)
                Console.WriteLine("You win");
            else
                Console.WriteLine("You lost\nThe lucky number is " + randomNumber);*/

            // exercise - 5
            Console.Write("Enter numbers seperated by couma : ");
            string numbersInCouma = Console.ReadLine(), temp = "";
            string[] copy = new string[numbersInCouma.Length];
            int count = 0;
            for (int i = 0; i < numbersInCouma.Length; i++)
            {
                if (numbersInCouma[i] == ',')
                {
                    copy[count] = temp;
                    temp = "";
                    count++;
                    continue;
                }
                temp = temp + Convert.ToString(numbersInCouma[i]);
                if (i + 1 == numbersInCouma.Length)
                    copy[count] = temp;
            }
            int MaxNum = 0;
            foreach (var i in copy)
            {
                if (MaxNum < Convert.ToInt32(i))
                {
                    MaxNum = Convert.ToInt32(i);
                }
            }
            Console.WriteLine("The maximum number is " + MaxNum);

            // exercise - 5 solved by mosh
            /*Console.Write("Enter commoa separated numbers: ");
            var input = Console.ReadLine();

            var numbers = input.Split(',');

            // Assume the first number is the max 
            var max = Convert.ToInt32(numbers[0]);

            foreach (var str in numbers)
            {
                var number = Convert.ToInt32(str);
                if (number > max)
                    max = number;
            }

            Console.WriteLine("Max is " + max);*/
        }
    }
}
```
# Arrays and lists
## Array
>Represents a fixed number of variables of particular type.
>
>In C# there is two types of array
>1. Single dimension
>2. Multi diemension
### Single dimension array
>The one dimensional array or single dimensional array in C# is the simplest type of array that contains only one row for storing data. It has single set of square bracket (“[]”). To declare single dimensional array in C#, you can write the following code.
```
var numbers = new int[5];
```
```
var numbers - new int[5] { 1, 2, 3, 4, 5 };
```
### Multi dimension array
>A multi-dimensional array in C# is an array that contains more than one rows to store the data.
>
>We have two types of multi dimensional array in c sharp
>1. Rectangular array
>2. Jagged array
>
#### Rectangular array
>In ractangular array each row has the exact same numbers of columns.
>##### Syntax (2D ractangular array)
```
var matrix = new int[3,5];
```
```
var matrix = new int[3,5]
{
    { 1, 2, 3, 4, 5 },
    { 6, 7, 8, 9, 10 },
    { 11, 12, 13, 14, 15 }
};
```
>Syntax for accesing a 2D array
```
var element = matrix[1,1];
```
>##### Syntax (3D ractangular array)
```
var colors = new int[3,5,4];
```
#### Jagged array
>In jagged array the number os columns in each row can be different.
>a diffrent way to look at jagged array is an array of arrays.
>##### Syntax
```
var array = new int[3][]; // 3 = 3 rows
array[0] = new int[4];
array[1] = new int[5];
array[2] = new int[3];
```
>This jagged array will looks like
>
>![2022-01-09](https://user-images.githubusercontent.com/92302123/148675027-e89f14a7-8211-470b-8e55-1594eaa9beaf.png)
>
>To access an element in this array
```
array[0][0] = 1;
```
#### Array properties
>![2022-01-09 (1)](https://user-images.githubusercontent.com/92302123/148675140-f86626fd-8f98-451f-9a32-a163a79975b9.png)
>##### Code of array properties
```
using System;

namespace arrays
{
    class Program
    {
        static void Main(string[] args)
        {
            var numbers = new[] { 3, 7, 9, 2, 14, 6 };

            // Length
            /*Console.WriteLine("Length : " + numbers.Length);*/

            // IndexOf()
            /*var index = Array.IndexOf(numbers, 9); // first parameter if array name and second parameter is value we have to found
            Console.WriteLine("Index of 9 : " + index);*/

            // Clear()
            /*Array.Clear(numbers, 0, 2); // first parameter is array name , second is starting index, and thirs is ending index
            foreach(var n in numbers)
            {
                Console.WriteLine(n);
            }*/

            // Copy()
            /*int[] another = new int[3];
            Array.Copy(numbers, another, 3); // 1st parameter is source array, 2nd parameter is destination array, 3rd parameter numbers of elemets we have to copy 
            foreach (var n in another)
            {
                Console.WriteLine(n);
            }*/

            // Sort()
            /*Array.Sort(numbers);
            foreach (var n in numbers)
                Console.WriteLine(n);*/

            // Reverse()
            Array.Reverse(numbers);
            foreach (var n in numbers)
                Console.WriteLine(n);
        }
    }
}
```
## Lists
>A list is an object which holds variables in a specific order. The type of variable that the list can store is defined using the generic syntax.
>
>The difference between a list and an array is that lists are dynamic sized, while arrays have a fixed size. When you do not know the amount of variables your array should hold, use a list instead.
>
>For using list we have to add namespace
```
using System.Collections.Generic;
```
>### Syntax
```
var numbers = new list<int>();
// you can also use this syntax
// List<int> numbers = new List<int>();
```
>### Initializing and declaring at same time
```
var numbers = new List<int>() { 1, 2, 3, 4 };
```
### Usefull methods in list
>1. Add()
>2. AddRange()
>3. Remove()
>4. RemoveAt()
>5. IndexOf()
>6. Contains()
>7. Count
### Full code of lists
```
using System;
using System.Collections.Generic;

namespace lists
{
    class Program
    {
        static void Main(string[] args)
        {
            var numbers = new List<int>() { 1, 2, 3, 4 };
            numbers.Add(1); // For adding an elemnent in list
             numbers.AddRange(new int[3] { 5, 6, 7 }); // adding list in list or array
            /*foreach (var n in numbers)
                Console.WriteLine(n);*/


            /*Console.WriteLine("Index of 1 : " + numbers.IndexOf(1)); // this will give first index of given number
            Console.WriteLine("Last Index of 1 : " + numbers.LastIndexOf(1));*/ // this will give last index of given number

            /*Console.WriteLine("Count: " + numbers.Count);*/ // this will tell how many elements in list

            /*numbers.Remove(1); // Removing first 1
            foreach (var n in numbers)
                Console.WriteLine(n);*/
            // if we want to remove all given number than we will use for loop (we can not use foreach because it will give error)
            /*for (var i = 0; i < numbers.Count; i++)
            {
                if (numbers[i] == 1)
                    numbers.Remove(numbers[i]);
            }
            foreach (var n in numbers)
                Console.WriteLine(n);*/

            numbers.Clear(); // it will clear all elements from list
            foreach (var n in numbers)
                Console.WriteLine(n);
        }
    }
}
```
# Date and time
>Date and Time in C# are two commonly used data types. Both Date and Time in C# are represented using C# DateTime class.
## Some functions of date and time (code)
```
using System;

namespace date_and_time
{
    class Program
    {
        static void Main(string[] args)
        {
            var dateTime = new DateTime(2015, 1, 1);
            var recentDateTime = DateTime.Now; // its return todays date and time both
            var today = DateTime.Today; // its only return todays date

            //Console.WriteLine("Hour: " + recentDateTime.Hour);
            //Console.WriteLine("Minuts: " + recentDateTime.Minute);

            var tomrrow = recentDateTime.AddDays(1); // it will return current date + 1day
            var yesterday = recentDateTime.AddDays(-1); // it will return current date 1 1day
            //Console.WriteLine(tomrrow);
            //Console.WriteLine(yesterday);

            Console.WriteLine(recentDateTime.ToLongDateString()); // return string in detailed Date
            Console.WriteLine(recentDateTime.ToShortDateString()); // return string in short Date
            Console.WriteLine(recentDateTime.ToLongTimeString()); // return string in detailed time
            Console.WriteLine(recentDateTime.ToShortTimeString()); // return string in short Date
            Console.WriteLine(recentDateTime.ToString()); // return string in detailed Date and time
            Console.WriteLine(recentDateTime.ToString("yyyy-MM-dd")); // date modifier
            Console.WriteLine(recentDateTime.ToString("yyyy-MM-dd HH:mm")); // date & time modifier
        }
    }
}
```
## TimeSpan
>C# TimeSpan struct represents a time interval that is difference between two times measured in number of days, hours, minutes, and seconds. C# TimeSpan is used to compare two C# DateTime objects to find the difference between two dates.
```
using System;

namespace Time_Span
{
    class Program
    {
        static void Main(string[] args)
        {
            // Creating
            var timeSpan = new TimeSpan(1, 2, 3); // arg1 = hours, arg2 = minuts, arg3 = seconds
            var timeSpan1 = new TimeSpan(1, 0, 0);
            var timeSpan2 = TimeSpan.FromHours(1);

            var start = DateTime.Now;
            var end = DateTime.Now.AddMinutes(2);
            var duration = end - start;
            Console.WriteLine("Duration " + duration);

            // Properties
            Console.WriteLine("Minutes: " + timeSpan.Minutes);
            Console.WriteLine("Total Minutes: " + timeSpan.TotalMinutes);

            // Add
            Console.WriteLine("Add example: " + timeSpan.Add(TimeSpan.FromMinutes(8)));
            Console.WriteLine("Subtract example: " + timeSpan.Subtract(TimeSpan.FromMinutes(2)));

            //ToString
            Console.WriteLine("ToString: " + timeSpan.ToString());

            // Parse
            Console.WriteLine("Parse: " + TimeSpan.Parse("01:02:03"));
        }
    }
}
```
# Working with text
## String
>### Formating
>ToLower() function convert string in lower case
>ToUpper() function convert string in upper case
>Trim() function trim whitespaces from string
>### Searching
>IndexOf('a') function return first index of given input from string
>LastIndexOf("hello") function return last index of given input from string
>### Substring
>Substring(startIndex) function create substring from given string
>Substring(startIndex, length) overloading same function
>### Replacing
>Replace('a', '!') function replace character/string in given string
>Replace("name", "mosh")
>### Null checking
>String.IsNullOrEmpty(str) function check string is empty or null
>String.IsNullOrWhiteSpace(str) function check string contain whitespace or is null
>### Splitting
>str.Split(',') function splite string. here i am splitting string with couma
>### Converting strings to numbers
```
string s = "1234";
int i = int.Parse(s);
int j = Convert.ToInt32(s);
```
>### Converting numbers to strings
```
int i = 1234;
string s = i.ToString(); // "1234"
string t = i.ToString("C"); // "? 1,234.00" Converting numbers in string(currency formate)
string t = i.ToString("C0"); // "? 1,234" Converting numbers in string(currency formate without floating point)
```
>#### Common formate specifiers
>![2022-01-16](https://user-images.githubusercontent.com/92302123/149665830-07bf548a-27e3-4fc0-bff5-3ae492959464.png)
>### Full code of string
```
using System;

namespace string_advance
{
    class Program
    {
        static void Main(string[] args)
        {
            var fullName = "Mosh Hamedani      ";
            Console.WriteLine("Trim: '{0}'",fullName.Trim()); // whitespaces are removed from front and begginning
            Console.WriteLine("ToUpper: '{0}'", fullName.Trim().ToUpper()); // converting string to upper case

            // firstname and lastname with substring method
            var index = fullName.IndexOf(' ');
            var firstName = fullName.Substring(0, index);
            var lastName = fullName.Substring(index + 1);
            Console.WriteLine("Firstname: " + firstName);
            Console.WriteLine("Lastname: " + lastName);

            // firstname and lastname with split method
            var names = fullName.Split(' ');
            Console.WriteLine("Firstname: " + names[0]);
            Console.WriteLine("Lastname: " + names[1]);

            Console.WriteLine(fullName.Replace("Mosh", "Moshfegh")); // replacing

            var nullString = "";
            Console.WriteLine(String.IsNullOrEmpty(nullString));

            var str = "25";
            var age = Convert.ToByte(str);
            Console.WriteLine(age);

            var price = 29.95f;
            Console.WriteLine(price.ToString("C"));
        }
    }
}
```
## Summarising text (code)
```
using System;
using System.Collections.Generic;

namespace Summarising_Text
{
    class Program
    {
        static void Main(string[] args)
        {
            var sentence = "This is going to be a really really really really really long text.";
            var summary = SummarizeText(sentence, 20);
            Console.WriteLine(summary);
        }
        static string SummarizeText(string text, int maxLength = 20)
        {
            if (text.Length < maxLength)
                return text;
            
            var words = text.Split(' ');
            var totalCharacters = 0;
            var summaryWords = new List<String>();

            foreach (var word in words)
            {
                summaryWords.Add(word);

                    totalCharacters += word.Length + 1;
                if (totalCharacters > maxLength)
                    break;
            }

            var summary = String.Join(' ', summaryWords) + "...";
            return summary;
        }
    }
}
```
## StringBuilder (String manipulator)
>String builder is  a class that is defined in the system that takes namespace and represents immutable string and makes it really easy and fast to create a string and modified on the fly.

>### Not for searching
>
>- IndexOf()
>- LastIndexOf()
>- Contains()
>- StartsWith() etc...

>### String manipulation methods
>
>- Append()
>- Insert()
>- Remove()
>- Replace()
>- Clear()

>For use some functions of string builder you have to add `using System.Text;`

>### StringBuilder (code)
```
using System.Text;
using System;

namespace String_Builder
{
    class Program
    {
        static void Main(string[] args)
        {
            var builder = new StringBuilder();
            builder.Append('-',10); // adding 10 '-'
            builder.AppendLine();
            builder.Append("Header");
            builder.AppendLine();
            builder.Append('-', 10);

            builder.Replace('-', '+'); // replacing '-' to '+'

            builder.Remove(0, 10); // removing 10 characters from 0 to 10

            builder.Insert(0, new string('-', 10)); // inserting '-' , 1st arg = index and 2nd arg is value

            // You can also write like this
            /*builder
                .Append('-', 10)
                .AppendLine()
                .Append("Header")
                .AppendLine()
                .Append('-', 10)
                .Replace('-', '+')
                .Remove(0, 10)
                .Insert(0, new string('-', 10));*/

            Console.WriteLine(builder);

            Console.WriteLine("First Char: " + builder[0]); // accesing character
        }
    }
}
```
## Programming types
### 1. Procedural programming
>A programming paradigm based on procedure calls.
### 2. Object-oriented programming
>A programming paradigm based on objects.
# Working with files
## Sytem.IO namespace
>For working with files you have to use `System.IO` namespace.
>
>some comman classes from System.IO
>1. File, FileInfo
>    - Provide methods for creating, copying, deleting, moving, and opening of files.
>    - Different between File and FileInfo
>      - FileInfo: provide instance methods
>      - File: provide static methods
>    - Some methods
>       1. Create()
>       2. Copy()
>       3. Delete()
>       4. Exists()
>       5. GetAttributes()
>       6. Move()
>       7. ReadAllText()
>2. Directory, DirectoryInfo
>    - Directory anf DirectoryInfo are very similar to File and FileInfo
>    - Different between Directory and DirectoryInfo
>       - DirectoryInfo: provide instance methods
>       - Directory: provide static methods
>    - Some methods
>        1. CreateDirectory()
>        2. Delete()
>        3. Exist()
>        4. GetCurrentDirectory()
>        5. GetFiles()
>        6. Move()
>        7. GetLogicalDrives()
>3. Path
>    - We also have the path class which provides methods to work with a string that contains a file or directory path information.
>    - Some methods
>        1. GetDirectoryName()
>        2. GetFileName()
>        3. GetExtension()
>        4. GetTempPath()
## File and FileInfo
> Code
```
using System;
using System.IO;
namespace file_and_fileinfo
{
    class Program
    {
        static void Main(string[] args)
        {
            var path = @"c:\somefile.jpg";
            File.Copy(@"c:\temp\myfile.jpg", @"d:\temp\myfile.jpg", true); // this will copy file one to another directory
            File.Delete(path); // this will delete file
            if (File.Exists(path)) // this will cheack whether given file is exist or not
            {
                //
            }
            var content = File.ReadAllText(path); // this will read all text from file and assign it to string

            var fileInfo = new FileInfo(path); // creating a object
            fileInfo.CopyTo("filename"); // copying file
            fileInfo.Delete(); // deleting file
            if (fileInfo.Exists) ;// this will cheack whether given file is exist or not
            {
                //
            }
        }
    }
}
```
## Directory, DirectoryInfo
> Code
```
using System;
using System.IO;

namespace Directory_and_DirectoryInfo
{
    class Program
    {
        static void Main(string[] args)
        {
            Directory.CreateDirectory(@"c:\temp\folder1"); // creating directory

            //var files = Directory.GetFiles(@"D:\vs code", "*.*", SearchOption.AllDirectories); // getting files names , 1st overload is path , 2nd is filter for files (here we used *.* its mean all files with all extention), and 3rd is give names of files all subdirectorys name
            //foreach(var file in files)
            //    Console.WriteLine(file);

            var directories = Directory.GetDirectories(@"D:\vs code", "*.*", SearchOption.AllDirectories); // getting files names , 1st overload is path , 2nd is filter for files (here we used *.* its mean all files with all extention), and 3rd is give names of all files of given directory name
            foreach (var directory in directories)
                Console.WriteLine(directory);

            Directory.Exists("name"); // cheacking directory exist or not

            var directoryInfo = new DirectoryInfo("path"); // creating directoryinfo
            directoryInfo.GetFiles();
            directoryInfo.GetDirectories();
        }
    }
}
```
## Path
> Code
```
using System;
using System.IO;
namespace path_in_cSharp
{
    class Program
    {
        static void Main(string[] args)
        {
            var path = @"C:Projects\CSharpFundamentals\HelloWorld\HelloWorld.sln";

            Console.WriteLine("Extension: " + Path.GetExtension(path));
            Console.WriteLine("File Name Without Extension: " + Path.GetFileNameWithoutExtension(path));
            Console.WriteLine("File Name: " + Path.GetFileName(path));
            Console.WriteLine("Directory Name: " + Path.GetDirectoryName(path));
        }
    }
}
```
