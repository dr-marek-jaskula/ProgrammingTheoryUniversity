## Host Api with SQL Database

- First create a resource group
- Then, create a Web App (this is App Service) with a App Service Plan 
- Go to our App Service and click "Get publish profile"
	- This will download a xml file with a profile specifications
	- In Visual Studio use "publish" and use "Import profile" and select the downloaded file
- Find SQL Databases and create an instance of a SQL Database (there is no free sql server)
- Go to the created resource and go to "Networking" to add IPs that we allow to contact to - just click "Add your client IPv4..."
- Also click "Allow Azure service and resources to access this server" in order to allow other app on Azure to reach this db (our api)
- Go to "Configuration"
- "New connection string" -> name it, paste the connection string from ADO.NET (from Azure Database service) and replace the password (write it there)
- Save and confirm the changes
- Now we can change the connection string in the appsettings.json (Azure will override the one in appsettings)
- Publish the application again (again download profile by "Get publish profile" and then click "new" and import profile and then publish)