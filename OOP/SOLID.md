## S - Single Responsibility Principle

"A class or method should have one responsibility/one reason to change".

We should use the dependency injection if we want to use other functionality. 

## O - Open-Closed Principle

"A class should be open for extensions and close for modification".

Adding the new cases or possibilities should be done without modifying the code.

## L - Barbara Liskov Substitution Principle

"Functions that use pointers or references to base classes must be able to use objects of derived classes without knowing it".

The derived class should only extend the base class.

The derived class must fully represent the base class (if we cast it to the base class, the representation should be proper).

There should not be a situation in which a inherited member is not reasonable to be used or can not be used in a derived class.

## I - Interface Segregation Principle

"Many client-specific interfaces are better than one general-purpose interface".

It is preferred to create multiple small interfaces rather than few big interfaces.

## D - Dependency Inversion Principle

"Depend upon abstractions, not concretions".

Hight level modules should depend on abstractions same as low level modules.