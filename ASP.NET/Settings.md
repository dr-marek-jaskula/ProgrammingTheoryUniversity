## Settings in ASP.NET Core

Settings and configurations in ASP.NET Core are stored in a "appsettings.json" file in the JSON format.
For instance, authorization settings, logging settings, corse policy.

In the appsettings.json we should not store the sensitive data, like connection string or security keys.
Sensitive data should be stored in Environmental Variables or secrets (but safe secrets like using docker secrets or github KeyVault)

To read the appsettings.json we need the "IConfiguration" interface that belongs to the Microsoft.Extensions.Configuration namepasce.
Instance of a class implementing this interface is injected from MVC Core Dependency Injection Container.

To get the object from the appsettings.json we just need to pass object's string name. If we need the nested property, we use the colon syntax.
> "ConnectionStrings:DefaultConnection"

Order of overwriting the settings:
> secrets > appsettings.json > appsettings.Development.json