# Tool to Debug Lambdas

To debug lambda locally use:

> aws-lambda-dotnet
> https://github.com/aws/aws-lambda-dotnet/tree/master/Tools/LambdaTestTool

It is also a test tool. Install it globally:

> dotnet tool install -g Amazon.Lambda.TestTool-6.0

and for .Net 7 (remember that AWS usually by default support LTS version of .NET), therefore use .NET 6 or .NET 8

To update the tool:

> dotnet tool update -g Amazon.Lambda.TestTool-6.0

To run the tool we can use (build solution before):

> dotnet lambda-test-tool-6.0

## Configure with Visual Studio 2022

1. Install extension "AWS Toolkit for Visual Studio 2022"

.NET Mock Lambda Test Tool will be automatically installed/updated and configured as a debug profile when you open a .NET Core Lambda project.

open a .NET Core Lambda project in Visual Studio and just push F5 to start debugging without any dependencies other than the AWS Toolkit for Visual Studio.

When a project is opened in Visual Studio the toolkit will detect the project is a Lambda project by looking for the 

```csproj
<AWSProjectType>Lambda</AWSProjectType>
````

property in the project file. 

If found it will write a launchSettings.json file in the .NET Core Lambda project's Properties folder. 

Visual Studio uses this file to look for debug profiles.

```json
{
  "profiles": {
    "Mock Lambda Test Tool": {
      "commandName": "Executable",
      "commandLineArgs": "--port 5050",
      "executablePath": "<home-directory>\\.dotnet\\tools\\dotnet-lambda-test-tool-6.0.exe",
      "workingDirectory": ".\\bin\\Debug\\net6.0"
    }
  }
}
```