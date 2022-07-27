## Refactorization 

This is a process of enhancing the code without changing the business logic.

## Cyclic reference

This is a situation in which two objects points to each other. 
This can be dangerous when serializing to json. The common solution is to create Data Transfer Objects (dto's) or use:

```csharp
builder.Services.Configure<JsonOptions>(options =>
{
    options.JsonSerializerOptions.ReferenceHandler = ReferenceHandler.IgnoreCycles;
});
```

## Object–Relational Mapper

It is a tool that allows us to translate the relational data to objects.

For instance: Entity Framework Core or Dapper are popular ORM's for C#, that additionally provide more functionalities.

## What is Version Control System

The purpose of version control is a tool that allows developers or software teams track changes in the codebase.
Moreover, the communication in the team is enhanced.

The most popular version control system is git.

## Git and GitHub

Git is a version control system.  
GitHub is a hosting service used to govern repositories.

## Deadlock

It is a situation in which at some tasks are waiting for each other to finish they jobs.

## Serialization and deserialization

This a process of converting the object in the program memory into a stream of bytes in order to save this data to the database or a file.
The aim of this process is to save the objects state in order to retrieve it if there is such need.

Deserialization is a revered process.

We also use word "serialization" to convert data formats, like from c# code to json file.
In C# we can serialize object by JsonConvert from NewtonsoftJson or JsonSerializer from System.Text.Json.Serialization.



