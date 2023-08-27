## Tools for .NET for AWS

### AWS Command Line Interface (CLI)

Download and install the CLI. Then configure the aws:

> aws configure

this will ask for 

1. access ID 
2. access key
3. default region name
4. default output format (use default json)

We can get this info from: 

a) Security Credentials
b) Users

### AWS PowerShell module

1. Install-Module -Name AWS.Tools.Installer 

then we can install concrete modules

2. Install-AWSToolsModule AWS.Tools.S3 -CleanUp

### Visual Studio For AWS

1. Extensions -> Online -> AWS Toolkit for Visual Studio

2. View -> AWS Explorer

Upload credentials (for instance form cvs file), then set the region.
