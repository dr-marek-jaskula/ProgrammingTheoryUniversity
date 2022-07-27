## Generic types

Generic types allow us to create classes or method that will work with wide range of data types.

Generic typed were created because of dynamic collections, which were less effective without generics, due to the boxing and unboxing.

Using the generics we can write code that is:
- reusable 
- strongly typed

## Generic constraints

Generic constraints allow to constrained types that will be passed to the generic classes or methods. 

We use the **where** keyword to create the limitation.

We can make a restriction that the type is a:
- class 
	- must be a reference type
- \<inteface name\> 
	- implement the interface
- \<base class name\> 
	- inherits for a class
- new() 
	- has parameterless constructor
- struct 
	- be a non-nullable value type, it implies new()
- notnull 
	- be a not-nullable type
- default 
	- use to override other generic method and set that they constraints of **class** and **struct** should be omitted

## Generics delegates

Generic delegates are predefined delegates types, to which we can pass the input types and output types.
They are usually used to pass anonymous functions (as lambda expressions) for instance to LINQ methods, so that our code will be more reusable.
There are three generic delegates:
- Action 
	- takes up to 15 parameters and does not return any value, just like a void
- Predicate 
	- takes up to 15 parameters and returns a boolean
- Func 
	- takes up to 15 parameters and returns a a specified type