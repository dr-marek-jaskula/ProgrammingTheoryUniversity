## DotNetLambdaCLI

This is a global dotnet cli tool.

To install it use: 

> dotnet tool install -g Amazon.Lambda.Tools

To update it use:

> dotnet tool update -g Amazon.Lambda.Tools

To deploy lambda function use: 

> dotnet lambda deploy-function MyFunction --function-role role

To invoke lambda function with input (payload) use: 

> dotnet lambda invoke-function MyFunction --payload "Just Checking If Everything is OK"

