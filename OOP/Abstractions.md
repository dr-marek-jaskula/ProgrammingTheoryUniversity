### Abstract class

Abstract class is a *half defined* parent class. The full definition is provided by child classes.

- Abstract classes can not instantiate an object, but they can contain a constructor.
- Abstract classes can contain non-abstract and abstract methods.
	Every abstract method needs to be overridden in a non-abstract child class.
- Abstract methods are **virtual**
- Abstract methods must be overridden and they can not have default implementation.
- Abstract classes are inherited. Therefore, only one abstract class can be inherited.

If the abstract class contains only pure public abstract members (methods and properties), then it similar to the interface. Nevertheless, in C# is it a bad design.

### Interface

Interface is a **contract** - if it is broken, it has visible impact, so a developer would notice this. 
Contract is between the developer who is creating a class and the consumer that is using the class. 
Every class that implement the interface will follow the interface structure.

Interfaces provides just signatures. Interfaces are kept without logic, so the developers can focus on abstraction.

- All interface members are public and they can not have other access modifier
- Interfaces can have only properties and methods (also static) 
- Interfaces are implemented. Therefore, multiple interfaces can be implemented into one class
- Starting from C# 8.0 the interface can have the default implementation, but this should be extremely rarely used
- Naming convention for interface is to start the name of interface from 'I'
- We can implement an interface into the abstract class or to the other interface
- We can not create a instance of a interface
- We can not make that interface inherit from a class.

The biggest benefit of a interfaces is that they allow the inversion of control (dependency inversion).

Instead of changing the interface, we should create a new interface and the new interface should implement the old one.
We can do it for versioning.

**Interface Segregation Principle**:
> It is preferred to created many small interfaces, rather then few big ones.