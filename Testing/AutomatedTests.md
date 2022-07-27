## Automated tests

Automated tests are tests that automates the testing process. 

They consist of:
+ Unit Tests (70% of all tests)
+ Integration Tests (20% of all tests)
+ End-To-End Tests (E2E) (10% of all tests or less)

The most popular library for automated tests is xUnit.

## Conventions

Test method should be named in the following manner:
> public void MethodToTest_TestScenario_ExpectedResult()

They should be structured in a following manner:

```
//Arrange

//Act

//Assert
```

We can also use "expectedResult" and "actualResult" terminology.

## Advantages

Advantages of testing are:
- Save time (less time spend for debugging and looking for errors)
- Automation (we can run tests at night or after push)
- Documentation (tests can be used for documentation purposes, because they show how pieces of code works)
- Quality (tested code is better code)
- Forcing to apply proper principles and design patterns

## Test Libraries

Testing libraries:
- xUnit (it is a new one made by nUnit creators, Microsoft uses also xUnit)
- nUnit
- MSTest

Mocking libraries:
- Moq
- NSubstitute
- FakeItEasy

Assertion libraries:
- Fluent Assertion
- Shouldly

My preferred libraries:
xUnit + NSubstitute + Fluent Assertion