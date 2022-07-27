## Equals
 
It is a C# method that returns a boolean value based on compare.

Every object in C# has this method.

This method compares **values** with the given input object:
> obj.Equals(otherObj);

## ReferenceEquals
 
This is a static method and takes two **reference** type parameters and compare references.

ReferenceEquals is not throwing any exception.
 
> Object.ReferenceEquals(obj, otherObj);

## ==

It is used to compare object **reference** equality. 

However, when the value is immutable, then the operator is overwritten for comparing values.

For instance, the "==" operator for strings was overwritten to compare values.

## is

Keyword **is** checks if the result of an expression is compatible with a given type.

For example:
> expression is type  
> iBoxed is int

It can be useful in such situations in a if or switch statement:
> myObject is int b  
> input is null