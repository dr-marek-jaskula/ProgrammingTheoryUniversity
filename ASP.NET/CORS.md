## CORS

Cross-Origin Resource Sharing is a mechanism of sharing the resources between different servers. 
For instance, between application **backend** and **frontend**.

In ASP.NET Core we configure CORS as follows:

```csharp
builder.Services.AddCors(options =>
{
    //Name of the policy needs to be the same as the name of the Cors policy in the configuration region
    options.AddPolicy("FrontEndClient", policyBuilder =>
    {
        policyBuilder
        .AllowAnyMethod()
        .AllowAnyHeader()
        //In "appsettings.json" we determine what hosts are allowed. To allow all origins we use '*'
        .WithOrigins(builder.Configuration["AllowedOrigins"]);
    });
});
```