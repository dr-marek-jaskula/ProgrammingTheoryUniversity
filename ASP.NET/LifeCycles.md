# Life cycles in ASP.NET Core

There are three types of life-cycles in the ASP.NET Core:
- Transient
- Scoped
- Singleton

## Transient

*AddTransient* method instantiates **one** object per **each** occurrence of the dependency injection in **each** class related to the controller action
that handles the request.

If there are more parameters of certain class type, multiple different instances will be created.

## Scoped

*AddScoped* method instantiates **one** object per request. 
When the request appears, the object is created. 
When the request is done, the object is destroyed.

Even if there are more parameters of certain class type, only the one object will be created.

This approach is used commonly, for instance for database contexts or services.

## Singleton

*AddSingleton* method instantiates **only one** instance per **whole** application.
Singleton is like a global object.

This approach is rarely used, for instance for configurations objects or loggers. But we can use it also for a spell checker.

It should be used with caution, because it can be shared between different threads.

## Life cycle detail (Singleton)

If we register multiple singletons of the same interface, the last one is used and the other ones are hidden. 
To verify this statement we can inject (by Dependency Injection) the IEnumerable of a singleton type.