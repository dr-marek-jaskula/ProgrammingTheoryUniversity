## Common Language Infrastructure (CLI)

It is an open specification and technical standard developed by Microsoft. 
It enables an application, written in any of commonly-used programming languages, to run on any operating system, using a common runtime program rather than a specific for each language. 

Common Language Infrastructure contains 4 features:
- Common System Type (CTS)
- Common Language Specification (CLS)
- Metadata
- Virtual Execution System (VES)

The .NET framework implements the Common Language Infrastructure.

## Common Type System (CTS)

In languages that uses .NET, like C# or VB.NET, we have different types. For instance, in C# there is *int* and in VB.NET we have *Int32*.
Therefore, there was a need to standardizes types. The system responsible for this task is called Common Type System (CTS).
To sum up, .NET has own data types and at the end of the day, each variable is translated into one of these types.

## Common Language Specification (CLS)

Types in .NET are handled by CTS, but there are still major differences between programming languages in .NET like:
- C# is case-sensitive ("int i = 0;" is not the same as "int I = 0;") 
- VB.NET is not case-sensitive ("Dim i AS Integer" is the same as "Dim I AS Integer")  
Moreover, some languages are functional, some have pointers and others do not use pointers.

Therefore, there was a need to create a set of guidelines, like "do not use case-sensitives", "do not use pointers".
By them, we could consume VB.NET code inside C#, C# inside F# and so on.

Such set of guidelines is CLS.  
When any .NET programming language follows this set of rules it can be consumed by any other language that follows the .NET specifications

## Metadata

Metadata describes all classes and class members that are defined in the whole assembly. 
Moreover, metadata describes the classes and class members that current assembly calls from external assemblies.

A compiler will generate the metadata and store them in the assembly containing the IL code. 
When the runtime executes, it makes sure that the metadata of the called method are the same as the metadata that are stored in the calling method. 
This ensures that a method can only be called with exactly the right number of parameters and proper parameter types. 

Metadata can be added to the code through attributes.

## Virtual Execution System

Virtual Execution System is a runtime system of the Common Language Infrastructure, which provides an environment for executing managed code. 

To a large extent, the purpose of the VES is to provide the support, required to execute the Intermediate Language instructions set. 

The Common Language Runtime (CLR) implements the VES as defined in the Common Language Infrastructure standard.  
So the VES is like an interface for a runtime. 

##  Just In Time compiler (JIT)

The JIT compiler runs after the program has started and compiles the code on the fly (or just-in-time, as it is called) into a form that is faster, typically the host CPU's native instruction set.
So when you run your program, the IL is compiled, using the Just In Time (JIT) compiler (a process often called JIT’ing). 
The result is machine code, executed by the machine’s processor. 

The JIT has access to dynamic runtime information, whereas a standard compiler does not. Therefore, it can make better optimizations, like inlining functions that are used frequently. Traditional compiler compiles all the code to machine language before the program is first run.

The standard JIT compiler runs on demand. When a method is called, the JIT compiler analyzes the IL and produces highly efficient machine code.

## Intermediate Language (IL)

Intermediate Language is a partially converted code. The JIT compiler compiles IL into the machine code in a optimized manner.

C# is a hight level language. Therefore, it needs to be converted into the machine language (called also native language. 
However, C# code is not directly converted into the Machine Language like other C languages.
At first it is converted into the **partially converted code** (Intermediate Language).
Then, the IL is converted into the machine language by the JIT compiler, invoked by CLR.

C# code is compiled into IL when the project is built. The IL is saved in a file on disk.

It is **possible** to view the IL code using such tools like "IL Spy".

> C# Code > C# Compiler > IL > .NET Runtime > JIT Compiler > machine code > Execution

## Benefit of compiling the code into IL

Development and production environments are usually different.
Therefore, the Machine Language should be optimized by taking into account the Operating System.

Due to the fact that .NET languages are firstly converted into the IL, the JIT compiler, depending on the OS, is able to optimize the further compilation to the Machine Language.
In the end, the application performance is enhanced.

## Common Language Runtime (CLR)

It is a Virtual Execution System (runtime execution) of .NET. It helps to execute the .NET applications.  
Primary is used to:
- Invoke the JIT, to compile the Intermediate Language into the Machine Language.
- Provide the Garbage Collector, Exception Manager, Thread Support, Type Checker, Debug Engine (and more)

Code that is executed under CLR execution environment, like C# code, is called as **managed code**.

**Unmanaged code** is code that is executed outside the boundary of CLR, like C Language code. So the unmanaged code is the code that executes under the supervision of the Operating System (ex: COM components).

## Garbage Collector (GC)

Garbage Collector is the background progress that is running continuously. Its task is to release the unused managed resources.
In Visual Studio 2022 we can use **Profiler** to examine the GC work.

In .NET for normal **memory leaks**, that can occur for instance in C++.
Nevertheless, we can still create objects that our application does not need, but the GC thinks it still does. 
This can only happen because these objects are referenced by our application in one way or another.

The GC divides the memory into three spaces called **generations**: 
- Generation 0
- Generation 1
- Generation 2

When the object is created, it is by default assigned to the Generation 0, unless it is bigger than 85KB - if so then it is assigned straight to Generation 2.
The idea of the Generation 0 is to hold the short-living objects.

Garbage Collector starts claiming objects from the Generation 0. Objects that survive the GC are moved to the Generation 1.
Then, GC claims Generation 1 and surviving objects are moved to the Generation 2. The idea of Generation 2 is to hold the long-living objects.

User can only allocate objects to generation 0 (SOH: Small Objects Heap) or the generation 2 (LOH: Large Objects Heap).
Only the GC can "allocate" objects to generation 1 (by promoting survivors from generation 0) and generation 2 (by promoting survivors from generation 1).

This algorithm was built on the assumptions that long-living objects are rarely abandoned but the new objects are most likely to be short-living.

Garbage Collector does not release the external resources like database connections.