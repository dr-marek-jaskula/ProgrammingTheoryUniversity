## Identity Access Management

Determine the access to the resources. 

1. Identities (who requests)
	a) Users
	b) Groups
	c) Roles
	d) Credentials

2. Permissions (what is requested by the identity) 
	a) Policies -> Statements

Example:

a) Users: Arnold, Tom 
b) Groups: SeniorDevs
c) Roles: S3FullAccess 
d) Policies: 
```json 
{
  "Version": "2023-05-13",
  "Statement":[
    {
      "Effect": "Allow",
      "Action": [
        "s3:*",
        "s3-object-lambda:*"
      ],
     "Resource": "*"
    }
  ]
}
```

where SeniorDevs group has Arnold and Tom, and Role S3FullAccess is bind to above policy.

If the next user "Adam" joins the company and we want to just give him a read only access 
we create a new role just for him.

Role: AmazonS3ReadOnlyAccess

Then we bind the role with new policy:
```json
{
  "Version": "2023-05-13",
  "Statement":[
    {
      "Effect": "Allow",
      "Action": [
        "s3:Get*",
        "s3:List*",
        "s3-object-lambda:Get*"
        "s3-object-lambda:List*"
      ],
     "Resource": "*"
    }
  ]
}
```

## Proper Approaches

1. Do not use root user if possible. Create new user to certain tasks.
2. Use Multi Factor Authentication
3. Follow Least-Privilege model (give only privileges that are required for a users task)
4. Be careful when changing policies

## Credentials

1. Local Development
    a) Shared AWS Credentials between IDEs/CLIs and Debugging Apps
    b) BasicAWSCredentials stored in Configuration (appsettings.json)
    c) SDK Store (only on Windows, but encrypted)

2. Production
    a) IAM Roles 

## Create new User

Go to Security Credentials -> Users -> Add User -> determine name and check "Access key - Programmatic access"

Then attach existing policies or add user to the group, or copy permission from existing user.

We can also create new policy or add a permission.

How to use:
1. appsettings.json
```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning"
    }
  },
  "AllowedHosts": "*",
  "AccessKey": "accessKey",
  "AccessSecret": "secretKey"
}

```

Inject config and use them
```csharp
_clinet = new AmazonDynamiDbClient(new BasicAWSCredentials
(
    _configuration.GetValue<string>("AccessKey")
    _configuration.GetValue<string>("SecretKey")
);
```

#### Encrypt using AWS Explorer


We can encrypt these values in appsettings by using the AWS Explorer.

1. Add new profile 
2. Change storage location to ".NET Encrypted Store"
3. Import the csv with credentials (or paste them)
4. Specify region

Then, we can remove "AccessKey" and "AccessSecret" from appsettings.json and use just:

```csharp
_clinet = new AmazonDynamiDbClient();
```

5. At first we need to setup the SDK in program.cs

```csharp
//Get AWS profile information from configuration providers
AWSOptions awsOptions = builder.Configuration.GetAWSOptions();
//Configure AWS service clients to use these credentials
builder.Services.AddDefaultAWSOptions(awsOptions);
//AWS service clients will be a singleton by default
builder.Services.AddAWSService<IAmazonDynamoDB>();
```

And the key will be encrypted.