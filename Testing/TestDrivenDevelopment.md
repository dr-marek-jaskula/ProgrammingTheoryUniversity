## Test Driven Development (TDD)

This is an approach of creating an application. It says that we should:
+ Firstly, write the test (test will be *red*)
+ Secondly, write the system under test in the raw form (just to make test *green*)
+ Refactor the code if possible or write other functionalities

Cycles:
> Red -> Green -> Refactor

### Opinion

Be pragmatic not dogmatic.

TDD approach should be used with caution - not all pieces of code should be tested, but only these that are complicated or crucial.

Too much testing results in wasting time - doing unnecessary work or making more complicated tests then the tested logic.

Use TDD approach only for business logic, like when creating services in ASP.NET Core.
