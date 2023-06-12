## Naming Project

General naming convention:
\<ProjectNameToTest\>.Tests.\<TypeOfTestProject\>

Types of test projects:
+ Unit
+ Integration
+ UI
+ E2E
+ Performance

For unit test of project CalculatorLibrary
> CalculatorLibrary.Tests.Unit

## Test Class Naming

General naming conversion:
\<ClassNameToTest\>Tests
> CalculatorTests

## Test Method Naming

My naming conversion:
\<MethodToTestName\>_Should\<ExpectedResult\>_When\<TestScenario\>

> GetById_ShouldReturnProduct_WhenProductExists

For parameters and results:
- expected
- actual

or

- expectedResult/expectedUsers/etc.
- actualResult/actualUsers/etc.

## System Under Test

System Under Test is the system we test.

For instance, it can be a "calculator" class.

## Mock

Mocks should end with "Mock" suffix:

> _productRepositoryMock
