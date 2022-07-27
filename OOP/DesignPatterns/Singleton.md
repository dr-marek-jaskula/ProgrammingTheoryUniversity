## Singleton

Singleton pattern restricts the instantiation of a class to a single instance.
It make the object globally available.

Singleton can be an anti-pattern. It can be used to much and by that cause problems.

Well-known use cases are: configuration object or logger (or we can use for SymSpell).

Problems with singleton:
+ Thread safe (additional code) 
+ Encapsulation (additional code) 
+ Iterator (additional code)
+ Validation (additional code)

```csharp
public static class Singleton
{
	// 1. encapsulate
	private static IEnumerable<Country> _countries = null;

	// 3. Safe iteration (only IEnumerable methods are available)
	public static IEnumerable<Country> GetCountries()
	{
		// 2. Validation
		if(_countries == null)
		{
			_countries = new IEnumerable<Country();
		}
		return _countries; 
	}
	public static void RefreshCountries()
	{
		// Thread safety
		lock(_countries)
		{
			_countries = new IEnumerable<Country>();
		}
	}
}
```

It can be hard to test Singletons, because of the state. We would need to clear the state each time we test it (i.e. test should clear it at the beginning)

Singleton pattern breaks:
- Single Responsibility Principle (business logic and its own initialization) 
- Open-Closed Principle (we must modify code if we want to extend its abilities)

Moreover, it makes hard coupling (breaks loosely couped module)

## Singleton is ASP.NET

If we register multiple singletons of the same interface, the last one will be used and the other ones will be hidden. 
To verify this statement we can inject the IEnumerable or registered singleton.

## Example

Configuration objects:

```csharp
public class Configuration
{
	private static Configuration? _instance = null;
	private static readonly object _lockObject = new();

	public string StringProperty { get; set; } = string.Empty;
	public int IntProperty { get; set; }

	private Configuration()
	{
	}

	public static Configuration GetInstance()
	{
		lock (_lockObject)
		{
			if (_instance == null)
				_instance = new Configuration();
		}

		return _instance;
	}
}
```