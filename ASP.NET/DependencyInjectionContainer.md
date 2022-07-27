## Dependency Injection Container in ASP.NET Core

DI Container enables to register types as interfaces or classes. When the certain interface (or class) is required, then the specified class is injected.

In order to register the type in the DI Container we can use one of three methods:
- AddSingleton
- AddScoped
- AddTransient

Depending on the method we choose, the injected object will have different life time period.

DI Container can also be used for mocking purposes.