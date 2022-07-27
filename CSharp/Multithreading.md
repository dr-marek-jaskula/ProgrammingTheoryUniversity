# Multithreading

## Threads

Threads help to executed the code is the parallel manner:

Drawbacks:
- Even if the new threads are spawned, all of them by default use the same processor.
	In order to make them using different processor we need to write an additional code.
- Creating and deleting the new thread is an expensive process.
	Therefore, we could use the **thread pool**, approach that will result in not deleting threads and reusing them if necessary.
- Thread can not return the result by default.
	To get the result we would need to use delegates and events.

## Tasks Parallel Library (TPL)

Task does parallel processing. Task will be spawn to run of different processors (use not loaded processors).

Advantaged:
- Tasks use parallel processing (use multiple processors by default)
- Tasks use **thread pool** approach (called **pooling**)
- Tasks can return the result
- Tasks can be canceled (using the cancellation token)
- Tasks can be used with the **async** - **await** keywords
- Tasks can be chained (one task can invoke the next one)

Preferred way is to use Task if it is possible (Threads only for legacy code).

## **async** and **await** keywords

**async** and **await** are keywords that help us to write an asynchronous code.

Asynchronous code is the code that do not block the main thread. 
Moreover, in a application that renders the user interface, it will not stop the app execution.

Method that is **async** must contain **await** keyword and be of type: 
- void (not preferred, because we cannot catch exception from async void)
- Task
- Task\<T\>
- ValueTask
- ValueTask\<T\>

The *Main* method can be async method from C# 7.2.

Since C# 8.0 we can use the *IAsyncEnumerable* (and it generics) that can be use for streaming and much more.
*IAsyncEnumerable* was introduced to deal with problem of **yield return** for async methods.
The return type of method containing **yield return** needs to be *IEnumerable*, so for async methods the *IAsyncEnumerable* was created.

Then, we can await foreach loop, if the object we are iterating through is an IAsyncEnumerable.

## Parallel method execution

In order to execute multiple methods in parallel manner, we can use:
- Task.WhenAll()
	- awaiting this method: when all method finish executing, then WhenAll will be finished.
- Task.WhenAny()
	- awaiting this method: when any of given methods finish executing, then WhenAny will be finished.

We can pass any number of parameters to this asynchronous method and they will be executed in a parallel manner.

## Exception catching from the async method

Catching exceptions form the async method is possible only for:
- Task
- Task\<T\>
- ValueTask
- ValueTask\<T\>

It is not possible for void (void will result in crashing the app, even if the try-catch block was applied).

## **lock**

Lock instruction is used to prevent multiple threads to enter the piece of code.

```csharp
private readonly object lockObject = new object();

public void CriticalMethod()
{
	lock (lockObjec)
	{
		//only one thread can be here
	}
}
```

## ValueTask

ValueTask is either value or a task. It is commonly used when caching occurs:
- if the value is not cached, then it is get from a external source. Result will be a Task
- if the value is cachech, then it is obtained from a cache. Result will be a value.

ValueTask can improve performance.

We can not await ValueTask twice.