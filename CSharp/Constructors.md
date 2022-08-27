# Constructors

Constructor is the class member function that is invoked when the instance of a certain class in created. 
Constructor has the same name as a class name and does not have any return type.
It can be used to initialize the default values or inject dependencies. 

Constructor types:
- Default constructor
- Parameterized constructor
- Copy constructor
- Static constructor
- Private constructor
  
## Default constructor

This is the parameterless constructor. If there is no constructor defined, the default constructor is created by the compiler. 

## Parameterized constructor

This is the common constructor, created by the developer with at least one input parameter. One class can have multiple parameterized constructor with different signatures.

## Copy constructor

This is the constructor that initialized objects variables using the other object of same type, that was passed in by the parameter. 

> public Class_name(Class_name input) { //some code}

## Static constructor

Static constructor is a constructor that is executed at the compilation process.

There can be only one static constructor.

Static members can be initialized using the static constructor.

## Private constructor

Constructor can be marked as private. Such constructor can not be called outside the class. 

Private constructors are useful in cases where it is undesirable for a class to be created by code outside of the class.

- private constructor can be use for a Singleton pattern:

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

In above example only the "GetInstance" method is allows to create the instance of this class.

- private constructor can be useful when using a factory pattern:

```csharp
public class MyClass
{ 
    private static Dictionary<object, MyClass> cache = 
        new Dictionary<object, MyClass>();

    private MyClass() { }

    public static MyClass GetInstance(object data)
    {
        MyClass output;

        if(!cache.TryGetValue(data, out output)) 
            cache.Add(data, output = new MyClass());

        return output;           
    }
}
```

- it can be also used to create a "base" constructor that is called by other constructors:

```csharp
public class MyClass
{
    private MyClass(object data1, string data2) { }

    public MyClass(object data1) : this(data1, null) { }

    public MyClass(string data2) : this(null, data2) { }

    public MyClass() : this(null, null) { }
}
```

## Internal constructor 

Internal constructor is used mostly in the Domain Driven Design approach, to prevent calling the constructor from the external project.