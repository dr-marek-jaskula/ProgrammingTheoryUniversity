## JSON

JavaScript Object Notation is the file format in which we can store the serialized objects in form of key-value pairs (arrays can be stored using []). 

This is a lightweight way of storing data and is it the main data format used in front-end and back-end communication.
ASP.NET Core even implements the default serialization into the JSON format. Moreover, settings are also stored in .json format.

JSON does not use tags and is supported by javaScript. However the object in js is slightly different from JSON.

```
{
	"Name": "Shepard",
	"Level": 3,
	"IsAlive": true,
	"Statistics": [
		{
			"Name": "Strength",
			"Points": 14
		},
		{
			"Name": "Intelligence",
			"Points": 13
		}
	]
}
```

## XML

Extensible Markup Language.

This file format use tags, and is a structure it is similar to HTML.

```
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net6.0</TargetFramework>
    <ImplicitUsings>enable</ImplicitUsings>
    <Nullable>enable</Nullable>
  </PropertyGroup>

  <ItemGroup>
    <None Remove="Theory\CSharp\PopularQuestions.md" />
  </ItemGroup>

  <ItemGroup>
    <None Include="Theory\.NET\CommonLanguageInfrastructure.md" />
    <None Include="Theory\.NET\1.Introduction.md" />
    <None Include="Theory\.NET\3.Memory.md" />
  </ItemGroup>

</Project>

```



