## Eager Loading

This is a process of loading the data with a related data at once. 

The way to obtain Eager Loading in Entity Framework Core is to use: 
"Include" and "ThenInclude" methods.

## Lazy Loading

This is a process of delaying the data loading to the point when we need this data. 
Therefore, no unnecessary data is loaded.

The easiest way to obtain Lazy Loading for Entity Framework Core is to use NuGet Package: 
> Microsoft.EntityFrameworkCore.Proxies 

and then configure it:
```csharp
.AddDbContext<MyCustomDbContext>(
	b => b.UseLazyLoadingProxies()
		.UseSqlServer(myConnectionString));
```

Next, we need to mark all relations as **virtual**.

## Explicit Loading

This is a process of loading the data first and then, after some time, loading the related data. 

The way to obtain Explicit Loading in Entity Framework Core is to use:
"Load" method both with "Entry" and "Reference"/"Collection" methods, that can be chained with "Query" method to add filters etc.

```csharp
//at first:
var avon = _context.Shops
            .Where(s => s.Name == "Avon")
            .FirstOrDefault();

//later on:
_context.Entry(avon)
    .Collection(s => s.Products)
    .Query()
        .Where(p => p.Price < 70)
        .FirstOrDefault(p => p.Name == "Clock");
```