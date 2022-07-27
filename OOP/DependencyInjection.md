## Dependency Injection

Dependency Injection is a practice of providing Dependent object from outside, rather than creating the new object inside a class.

We can make dependency injection using:
- Constructor (Constructor Injection)
- Method (Method Injection)
- Property (Property Injection)

Nevertheless, the Construction Injection is the most common and simple way to inject the dependencies. 

- By delegating object creating outside the class we decouple the system.
	We aim to have loosely coupled system.
	To achieve this we also should use the inversion of control: all should depend on abstraction.

## Dependency Injection in ASP.NET Core

To inject the dependency, firstly we need to register it in a dependency injection container and select the life-time an injected object.
To determine life-time, in program.cs, we use choose one of the following "builder.Services" methods:
- AddTransient
- AddScoped
- AddSingleton

We can register the "ServiceDescriptor" using: 
- interface (or base class) and the class that will be obtained when the instance is required.
- just a class, then if the class instance is required, the instance of the same class will be provided. 

The method generics are:
- TService
- TImplementation