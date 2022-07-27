## Exception Handling

Exception are handled using the try-catch or try-catch-finally block.
We can catch specified exceptions or generally an exception. We may use details from the caught exception.
Therefore, we can display to the user the well detailed standardized answer like the one obtained by "ProblemDetails" class.

The finally block will be executed no matter what, after the exception is handled or even if no exception was thrown. 
It can be used to free the resources.

#### Example exceptions

- DivideByZeroException
- NullReferenceException
- ArgumentException
- ArgumentOutOfRangeException
- IndexOutOfRangeException
- OverflowException
- StackOverflowException

## **throw** vs **throw exception**

- **throw** does not reset the stack trace. It preserves the stack trace.

- **throw exception** resets the stack trace (so our errors would appear to originate from HandleException).

So let us say that Source1 throws Error1 and it is caught by Source2 and then Source2 throws again. 

- **throw** preserves the stack trace. 
> Source1 Error + Source2 Error will be available in the stack trace.

- **throw ex** does not preserve the stack trace. 
> So all errors of Source1 will be wiped out and only Source2 error will sent to the client.

Example for **throw**
1) error 1 has occurred 
2) it was catched
3) error 2 has occurred
4) it was catched and then error 1 + error 2 are still in the memory (stack trace has been maintained)

Example for "throw exception"
1) error 1 has occurred 
2) it was catched
3) error 2 has occurred
4) it was catched and then only error 2 is in the memory (stack trace has not been maintained)
