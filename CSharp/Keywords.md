## **out** 

**out** keyword is used to pass a parameter of a method by a reference.
While C# functions by default return a single value, the **out** keyword can be used to have multiple return value.
Nevertheless, the tuples or anonymous objects can be used for the same purpose in a more elegant way.

**out** is similar to **ref**.

In case of **out** the parameter does not need to be initialized before it is passed. 
Even when it is initialized, its value still needs to be determined.

## **ref**

**ref** keyword is used to pass a parameter of a method by a reference.
The value of referenced variable needs to be initialized and it does not need to be determined in the method.

## **const**

**const** keyword is used to define a constant. The constant value can not be changed during the runtime and it needs to be known at compile time.
Therefore, it need to be declared and initialized at once. Constant is by default static. It can be public or private.
We can use const for math consts or absolute path and other constant variables.
We cannot use **const** for reference types that requires "new" keyword (string can be used).

## **readonly**

**readonly** keyword is used to define a readonly variable. Such variable can not be changed after it is initialized. 
The initialization can be done after the declaration (at runtime) - can be static or non static.
**readonly** variables are declared as instance variable and need to be assigned in a constructor (cannot be undeclared after the object is created).
We can use **readonly** for reference types

## **static**

**static** keyword:
- can be used with **using** to since C# 6.0 to use the static members of a certain namespace without specifying a type name.
  - Example: use "using static System.Math;" for static math methods or constants.

- can be used for class members and classes itself, to determines that the object is known at compile-time.
  - static method or variable will be reachable without creating an instance of a class. Therefore, the single copy of an variable is created.
  - a static method cannot use the non-static members of a class. Therefore cannot use **this** keyword.
  - static class can contain only static members.

- can be used for constructor. Static constructor can be only one and it will be executed at the very beginning of the runtime process. 
  - static members can be initialized in a static constructor.

## **using** 

**using** keyword is used to import the namespace.  
We can use **static using** (described above)  
We can use **global using** to import namepsace for all assembly  

## **using** statement

For resources that requires disposing (releasing the memory), for instance db connection, we can use the **using** statement to properly dispose the
memory. When the program goes out of the using scope, the dispose method is called. So we can use this only for types that implement the *IDisposable* 
interface. 

*using statement* is just a try-finally block.

## **yield**

There are two ways to use **yield**:
- **yield return**
- **yield break**

**yield return**:  
This keyword is used to return an iterator for certain elements. 
Each time, in method, we execute "yield return {element}", the same value will be returned immediately. 
Nevertheless, the method execution will not stop. Instead, the next elements will be returned, until all of them are done.

Iterator declaration needs to follow rules:
+ Return type needs to be:
	+ IAsyncEnumerable<T>
	+ IEnumerable<T>
	+ IEnumerable
	+ IEnumerator<T>
	+ IEnumerator
+ Declaration can not have **ref** or **out** keywords.
+ can not use in lambda expressions and anonymous methods.
+ can not use in methods that contain unsafe blocks.
+ yield return statement can not be located in a try-catch block.
+ yield return statement can be located in the try block of a try-finally statement.

**yield break**:  
You can use a yield break statement to end the iteration.

Usage: 
- to improve the performance, sometime it is better to return element one by one, especially for massive collections (in Unity)
- to get only these elements that are needed, and not more

## **is** vs **as**

**is** keyword is used to check if the given variable is of a certain type.  
**as** keyword is used to convert one reference type to another (or nullable types)  

**is** returns a boolean value - true if a variable is of given type and false otherwise.  
**as** returns a converted type or null if the conversation is not possible.  

**is** can be used for boxing and unboxing  
**as** is used only for conversion with **null** value  

## **with**

**with** was introduced for structs and anonymous objects in C# 10 for cloning the values with some changes.

Example for structs:
> var money = new Money() { Value = 10, Currency = "$" }; var money2 = money with { Value = 20 };

Example for anonymous objects:
> var someValue = new() { Value = 10, Name = "test" }; var someValue2 = someValue with { Value = 20 };
 
## **params**

**params** keyword is used to define the method with varying number of input parameters with the same type.

This keyword can be only used as a method last input parameter and it needs to be:
> params \<Type\>[] \<inputs\> 

like: 
> params int[] numbers

## **value**

**value** keyword is used in a setter to represent the value that is being set.

## **dynamic**

**dynamic** keyword is used to define variable that can change type during runtime.  
Dynamic types are ignored by compiler and catched by Dynamic Language Runtime.  
Dynamic type is used when dealing with the external source of data, for instance with XML data format.

## **sealed**

**sealed** keyword can be used for a class to prevent inheritance (look "ClassTypes").

Other use case is to use **sealed** keyword for a method (with **override** keyword) to say that this method can not be further overwritten.
So to prevent overriding a method of a class. To sum up, method that is declared with the keyword **sealed** is always used with combination of override keyword and 
no derived classes will be able to override this method.

## **event**

The subscriber-publisher design pastern was implemented into C# by **event** keyword.  
Publisher -> publish the event.  
Subscriber -> is notified that event is triggered.  

Events are user actions, like clicking a button.  
We can use EventHanlder to deal with the events.

## **lock**

Lock instruction is used to prevent mutiple threads to enter the piece of code.

```csharp
private readonly object lockObject = new object();

public void CriticalMethod()
{
	lock (lockObjec)
	{
		//only one thread can be here
	}
}
```