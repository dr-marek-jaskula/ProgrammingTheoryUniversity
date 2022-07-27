## LINQ

LINQ stands for "Language-Integrated Query". 
This is the library that enables to integrate external queries with C#, like SQL or XML queries.  
LINQ provides many extension methods for collections.

## Single vs First

First returns the first element that satisfies the given predicate.
	Otherwise, it throws an exception: *InvalidOperationExceptions*.

Single returns the element that satisfies the given predicate if such exits and there is not other element that satisfies the predicate.
	Otherwise, it throws an exception: *InvalidOperationExceptions*.

## SingleOrDefault vs FirstOrDefault

They are almost the same as Single vs First. The difference is:
- FirstOrDefault returns **default** (0 or null) if there is no element that satisfies the predicate.
- SingleOrDefault returns **default** (0 or null) if there is no element that satisfies the predicate.
	Nevertheless, it still throws an exception if there is more then one fitting elements.

We can define a custom default value for SingleOrDefault and FirstOrDefault methods.