## IQueryable

This is the type dedicated for ORM libraries, like Entity Framework, used to move the operations from the program memory to the database.
Therefore, to the program will obtain the results after sorting, filtering etc.

This enhances the performance of our application.

The IQueryable executes the query on the database side after it is needed to appear in the program. For example when we use "First()" or "ToList()".

## IEnumerable

All operations will be executed in the program memory.