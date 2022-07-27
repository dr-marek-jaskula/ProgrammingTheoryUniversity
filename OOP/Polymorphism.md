## Polymorphism

"Poly" means "many" and "morph" means "change per situation". 

It is an ability of different types to provide a unique interface for different implementations of methods.

- **overriding**, which involves inheritance and **virtual** functions, is called dynamic (runtime) polymorphism.
	- we use **override** keyword to override the method. We can use **base** keyword to use the base class method functionality.
- **overloading** is considered as static (compile-time) polymorphism. If we use only the definition from wikipedia, it is not a polymorphism.
    + it is present when the methods of the same name have different signatures.
	+ the operators can be overloaded: "public static MyClass operator +(MyClass arg1, MyClass arg2)". Here we need **operator** keyword
- **hiding** happens when the dynamic polymorphism is not present (and static is also not present). The hidden member still exists. Usually this approach is undesirable.
	therefore, it is preferred to use **new** keyword to hide a member, i.e. demonstrate that the hiding was intended.
	method hiding is also called **shadowing**.