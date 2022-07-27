## Class types

- static class
- sealed class
- partial class
- abstract class

## Static class

- Static class can have only static members
- Static class can not be instantiated 
- Static class in known at compile-time
- Static class can have only static constructor, where the static members can be initialized

We can use static classes for extension method.  

For instance, to create a method extending the *IServiceCollection* in ASP.NET, to register services.

## Abstract class

Abstract classes are described in OOP -> Abstractions

## Partial class

Partial class is a class with multiple definitions spread among different .cs files that together make one final definition. 

Partial classes are used mostly for the auto-generated code, for instance for custom migrations created by Entity Framework Core.

It is possible to create an abstract partial class.

## Sealed class

By default classes are not sealed.
We use **sealed** keyword to mark the sealed class.

- Sealed class can not be instantiated.
- Abstract classes can not be sealed
- Sealed classes can be extended

Sealing a class can be used when designing a utility class with fixed behavior, which we don't want to change.

When casting objects, the runtime must check the type of the object at runtime. 
When casting to a non-sealed type, the runtime must check for all types in the hierarchy. 
However, when casting to a sealed type, the runtime must only check the type of the object, so it is faster. In other words: the sealed keyword tells the CLR that there is no class further down to look for methods.
This results in a performance boost.

In most performance-enhancing tools on the market nowadays, there are checkboxs that will seal all classes that aren't inherited.